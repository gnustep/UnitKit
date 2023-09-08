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

FRAMEWORK_NAME = UnitKit
$(FRAMEWORK_NAME)_CURRENT_VERSION_NAME = 1.5
$(FRAMEWORK_NAME)_DEPLOY_WITH_CURRENT_VERSION = yes

$(FRAMEWORK_NAME)_OBJC_FILES = $(wildcard *.m)
$(FRAMEWORK_NAME)_HEADER_FILES = $(wildcard *.h)

# Use ARC
$(FRAMEWORK_NAME)_OBJCFLAGS = -fobjc-arc

# Localization files
$(FRAMEWORK_NAME)_LOCALIZED_RESOURCE_FILES = UKTestHandler.strings

include $(GNUSTEP_MAKEFILES)/framework.make
include $(GNUSTEP_MAKEFILES)/aggregate.make
