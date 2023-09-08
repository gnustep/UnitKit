# Copyright 2023 Hugo Melder
# 
# SPDX-License-Identifier: Apache-2.0
# This file is part of the UnitKit project.

# Check if GNUSTEP_MAKEFILES is set, if not, try to find it
ifeq ($(GNUSTEP_MAKEFILES),)
 GNUSTEP_MAKEFILES := $(shell gnustep-config --variable=GNUSTEP_MAKEFILES 2>/dev/null)
endif
ifeq ($(GNUSTEP_MAKEFILES),)
 $(error You need to source the GNUstep.sh script first, or set GNUSTEP_MAKEFILES to the location of the GNUstep Makefiles!)
endif

include $(GNUSTEP_MAKEFILES)/common.make

PRINT_PROJECT_NAME = NO

BUNDLE_NAME = TestBundle

$(BUNDLE_NAME)_BUNDLE_LIBS = -lUnitKit $(FND_LIBS)

$(BUNDLE_NAME)_OBJC_FILES = TestOne.m TestTwo.m TestThree.m
$(BUNDLE_NAME)_HEADER_FILES = TestOne.h TestTwo.h TestThree.h

$(BUNDLE_NAME)_OBJCFLAGS += -fobjc-arc

include $(GNUSTEP_MAKEFILES)/bundle.make