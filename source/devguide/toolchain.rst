Toolchain
=========

Java SDK
--------

JavaCard is based on Java, and so are most tools used for JavaCard development. As such you will need a recent JDK, which means OpenJDK or the Oracle JDK.

JavaCard Kit / SDK
------------------

At the moment you will need the so-called JavaCard Kit, a closed-source toolkit published by Oracle that contains a CAP converter and verifier, the JavaCard class libraries and various other tools.

The CAP converter is used to transform a set of Java class files, all in the same Java package, into a CAP file. This CAP file contains a space-optimized converted form of the code and definitions in those class files. It also contains metadata that defines JavaCard applets. These CAP files can be loaded onto a JavaCard device for eventual execution.

The CAP verifier is responsible both for checking the consistency of converter output and verifying that the Java code provided is valid JavaCard code. It will check code and data references, verify that only supported types are used, the structure of the CAP file, validity of used opcodes and so on.

GlobalPlatform Client
---------------------

To load and install code to your card or token you will also need a GlobalPlatform client implementing the host side of the GlobalPlatform card specification. This client will also allow you to manage the security keys of the card and perform other management operations such as locking the card.

JavaCard Simulator
------------------

There exist both proprietary and open-source simulators for JavaCard environments that can be used for development and testing.
