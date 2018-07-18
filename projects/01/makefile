TARGETS := And \
           And16 \
           DMux \
           DMux4Way \
           DMux8Way \
           Mux \
           Mux16 \
           Mux4Way16 \
           Mux8Way16 \
           Not \
           Not16 \
           Or \
           Or16 \
           Or8Way \
           Xor
CHIPS = $(TARGETS:=$(CHIP_EXT))
ALLCHIPS = $(wildcard *$(CHIP_EXT))
TESTS = $(TARGETS:=$(TEST_EXT))
OUTPUTS = $(TARGETS:=$(OUT_EXT))
CHIP_EXT := .hdl
TEST_EXT := .tst
OUT_EXT := .out

TEST_COMMAND := $(CURDIR)/../../tools/HardwareSimulator.sh 
SUBMISSION := project1.zip

.PHONY: $(TARGETS) alltests clean submit

$(OUTPUTS):
	@$(TEST_COMMAND) $(basename $@)$(TEST_EXT) 2>&1

$(CHIPS): %$(CHIP_EXT) : %
$(TESTS): %$(TEST_EXT) : %

$(TARGETS):
	@$(MAKE) 2>/dev/null $@$(OUT_EXT) ; \
	exit_code=$$? ; \
	$(RM) $@$(OUT_EXT) ; \
	exit $$exit_code

alltests :
	$(info Running all tests)
	@( \
	for target in $(TESTS) ; do \
		printf "%-14s | " $$target ; \
		$(MAKE) 2>/dev/null $$target ; \
	done \
	)

submit: clean
	$(info Creating $(SUBMISSION))
	@zip $(SUBMISSION) $(ALLCHIPS)

clean :
	$(info Cleaning output files)
	@$(RM) $(OUTPUTS)
	@$(RM) $(SUBMISSION)
