# Copyright 2023 Hugo Melder
# 
# SPDX-License-Identifier: Apache-2.0
# This file is part of the UnitKit project.

# Check if GNUSTEP_MAKEFILES is set, if not, try to find it
.DEFAULT_GOAL := all

ifeq ($(GNUSTEP_MAKEFILES),)
 GNUSTEP_MAKEFILES := $(shell gnustep-config --variable=GNUSTEP_MAKEFILES 2>/dev/null)
endif
ifeq ($(GNUSTEP_MAKEFILES),)
 $(error You need to source the GNUstep.sh script first, or set GNUSTEP_MAKEFILES to the location of the GNUstep Makefiles!)
endif

include $(GNUSTEP_MAKEFILES)/common.make

SUBPROJECTS = UnitKit Tools

test::
	@echo "Running tests..."
	@$(MAKE) -C Tests
	@ukrun -q Tests/TestUnitKit/TestUnitKit.bundle

after-clean::
	@echo "Cleaning test data..."
	@$(MAKE) -C Tests clean

include $(GNUSTEP_MAKEFILES)/aggregate.make