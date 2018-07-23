PROJECT_CHIPS := ALU \
                 Add16 \
                 FullAdder \
                 HalfAdder \
                 Inc16

HELPER_CHIPS := 

TARGETS := $(PROJECT_CHIPS) $(HELPER_CHIPS)

ALLCHIPS = $(PROJECT_CHIPS:=$(CHIP_EXT)) $(HELPER_CHIPS:=$(CHIP_EXT))

TESTS := ALU.tst \
         ALU-nostat.tst \
         Add16.tst \
         FullAdder.tst \
         HalfAdder.tst \
         Inc16.tst

OUTPUTS = $(TESTS:$(TEST_EXT)=$(OUT_EXT))
CHIP_EXT := .hdl
TEST_EXT := .tst
OUT_EXT := .out

ifeq ($(shell uname -o),Msys)
	TEST_COMMAND := $(CURDIR)/../../tools/HardwareSimulator.bat
else
	TEST_COMMAND := $(CURDIR)/../../tools/HardwareSimulator.sh
endif
SUBMISSION := project2.zip

.PHONY: $(TARGETS) $(OUTPUTS) $(TESTS) alltests clean submit

$(OUTPUTS):
	$(TEST_COMMAND) $(basename $@)$(TEST_EXT)

$(CHIPS): %$(CHIP_EXT) : %
$(TESTS):
	@( \
		testResult=$$($(TEST_COMMAND) $@ 2>&1) ; \
		rm -f $@$(OUT_EXT) ; \
		echo $$testResult ; \
		[[ $$testResult =~ "Comparison ended successfully" ]] || exit 1; \
	)

$(TARGETS): % : %$(TEST_EXT)

alltests :
	$(info Running all tests)
	@( \
	failed=0; \
	success_msg="" ; \
	for test in $(TESTS) ; do \
		testResult=$$($(TEST_COMMAND) $$test 2>&1) ; \
		rm -f $$(basename "$$test" .tst).out ; \
		printf "%-14s | %s\n" "$$test" "$$testResult"; \
		[[ $$testResult =~ "Comparison ended successfully" ]] || ((failed++)); \
	done ; \
	exit "$$failed" ; \
	)

submit: clean alltests
	$(info Creating $(SUBMISSION))
	@zip $(SUBMISSION) $(ALLCHIPS)

clean :
	$(info Cleaning output files)
	@$(RM) $(OUTPUTS)
	@$(RM) $(SUBMISSION)
