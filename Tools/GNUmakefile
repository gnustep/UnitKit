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

TOOL_NAME = ukrun

$(TOOL_NAME)_OBJC_FILES = main.m

# Use ARC
$(TOOL_NAME)_OBJCFLAGS += -fobjc-arc
$(TOOL_NAME)_OBJCFLAGS += -I../

# Link against UnitKit
$(TOOL_NAME)_LDFLAGS += -L../UnitKit/UnitKit.framework -lUnitKit

include $(GNUSTEP_MAKEFILES)/tool.make
