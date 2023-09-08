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

BUNDLE_NAME = TestUnitKit
BUILD_DIR = $(CURDIR)/../TestFramework/TestFramework.framework/Versions/Current

# Set rpath to TestFramework without installing it
$(BUNDLE_NAME)_LDFLAGS += -Wl,-rpath=$(BUILD_DIR) -L$(BUILD_DIR)

$(BUNDLE_NAME)_NEEDS_GUI = no

$(BUNDLE_NAME)_BUNDLE_LIBS = -lUnitKit -lTestFramework $(FND_LIBS)

$(BUNDLE_NAME)_OBJC_FILES = $(wildcard *.m)
$(BUNDLE_NAME)_OBJCFLAGS += -fobjc-arc -I../

include $(GNUSTEP_MAKEFILES)/bundle.make

export TEST_BUNDLE_PATH = ../TestBundle/TestBundle.bundle 
export TEST_BUNDLE_LINK_PATH = ../TestUnitKit/TestBundle.bundle 

after-all::
	$(ECHO_NOTHING) \
	if [ ! -e $(TEST_BUNDLE_LINK_PATH) ]; then \
		ln -s $(TEST_BUNDLE_PATH) $(TEST_BUNDLE_LINK_PATH); \
	fi; \
	$(END_ECHO)

after-clean::
	rm -f $(TEST_BUNDLE_LINK_PATH)
