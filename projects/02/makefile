PROJECT_CHIPS := ALU \
                 Add16 \
                 FullAdder \
                 HalfAdder \
                 Inc16 \

HELPER_CHIPS := 

TARGETS := $(PROJECT_CHIPS) $(HELPER_CHIPS)

CHIPS = $(TARGETS:=$(CHIP_EXT))
ALLCHIPS = $(wildcard *$(CHIP_EXT))
TESTS = $(TARGETS:=$(TEST_EXT))
OUTPUTS = $(TARGETS:=$(OUT_EXT))
CHIP_EXT := .hdl
TEST_EXT := .tst
OUT_EXT := .out

ifeq ($(shell uname -o),Msys)
	TEST_COMMAND := $(CURDIR)/../../tools/HardwareSimulator.bat
else
	TEST_COMMAND := $(CURDIR)/../../tools/HardwareSimulator.sh
endif
SUBMISSION := project2.zip

.PHONY: $(TARGETS) alltests clean submit $(OUTPUTS)

$(OUTPUTS):
	$(TEST_COMMAND) $(basename $@)$(TEST_EXT)

$(CHIPS): %$(CHIP_EXT) : %
$(TESTS): %$(TEST_EXT) : %
$(TARGETS):
	@( \
		testResult=$$($(TEST_COMMAND) $@$(TEST_EXT) 2>&1) ; \
		rm -f $@$(OUT_EXT) ; \
		echo $$testResult ; \
		[[ $$testResult =~ "Comparison ended successfully" ]] || exit 1; \
	)

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
