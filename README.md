UnitKit
=======

This fork of UnitKit has improved GNUstep support, and aims to further improve the project.

Authors
: James Duncan Davidson, Nicolas Roard, Quentin Mathe, David Chisnall, Yen-Ju Chen, Christopher Armstrong, Eric Wasylishen

License
: Apache License 2.0 (see LICENSE document)

Version
: 1.5

UnitKit is a minimalistic unit testing framework that supports Mac OS X, iOS and 
GNUstep. 

The framework is less than 2000 loc, and built around two classes UKRunner and 
UKTestHandler, plus some test macros, and an empty protocol UKTest to mark test 
classes.

The UnitKit core features are:

- Test assertion macros
	- easy to write and read
	- without useless arguments
	- not too many ones
	- extensible (implement a UKTestHandler subclass or category)
- No test case class, just adopt UKTest protocol
- No special methods -setUp and -tearDown, just implement -init and and -dealloc 
- Class test methods in addition to instance ones
- Run loop integration for asynchronous testing
- Uncaught exception reporting
- Delegate methods to signal a test suite will start or just ended
- Tested method and class choice based on a regex
- Verbose and quiet ouput
- Optional ukrun tool to run test suites packaged in test bundles
- Xcode test suite templates

**Note:** This UnitKit version is a fork of the original UnitKit written by 
James Duncan Davidson. The original version is not available anymore, and its 
development has been halted for many years. The initial project web site 
unitkit.org is also no longer available.


Build and Install
-----------------

Read INSTALL.GNUstep.md documents.


Mac OS X support
----------------

Currently, only the GNUstep support is actively maintained. UnitKit should be compatible with
older versions of macOS and iOS, but it is not tested for newer versions. If you are interested in macOS support, please
open an issue or pull request.


How to use UnitKit with GNUstep Make
------------------------------------

You need to compile your sources as a bundle. Here is a GNUmakefile example:

    include $(GNUSTEP_MAKEFILES)/common.make

    BUNDLE_NAME = Test
    Test_OBJC_FILES = # your sources and test classes...
    Test_OBJC_LIBS = -lUnitKit # you can link a tested library or framework

    include $(GNUSTEP_MAKEFILES)/bundle.make

Then, just type:

	ukrun Test.bundle

And you should have the list of the tests and their status. You can omit the
'Test.bundle' argument, if you do so 'ukrun' will try to run any bundles (with 
.bundle extension) located in the current directory.
