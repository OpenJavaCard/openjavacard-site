Toolchain
=========

Java SDK
--------

JavaCard is based on Java, and so are most tools used for JavaCard development. As such you will need a recent JDK, which means OpenJDK or the Oracle JDK.

JavaCard Kit / SDK
------------------

At the moment you will need the so-called JavaCard Kit, a closed-source toolkit published by Oracle that contains a CAP converter and verifier, the JavaCard class libraries and various other tools.

The CAP converter is used to transform a set of Java class files, all in the same Java package, into a CAP file. This CAP file contains a space-optimized converted form of the code and definitions in those class files. It also contains metadata that defines JavaCard applets. These CAP files can be loaded onto a JavaCard device for eventual installation and applet usage.

The CAP verifier is responsible both for checking the consistency of converter output and verifying that the Java code provided is valid JavaCard code. It will check code and data references, verify that only supported types are used, the structure of the CAP file, validity of used opcodes and so on.

Build System
------------

While you can manually define build system rules to build your applets, you will most likely want to use a build system plugin.

Martin Paljak maintains the ant-javacard plugin for the ant build tool. We highly recommend this solution because it is quite lean and does not require online download of dependencies, which is a disadvantage in a secure development environment.

Fidesmo has published a workable gradle plugin for JavaCard. This solution is recommended for rapid development with some basic IDE integration.

In some cases you might wish to maintain build systems for both tools, allowing your users several options when they wish to use your applet.

GlobalPlatform Client
---------------------

To load and install code to your card or token you will also need a GlobalPlatform client implementing the host side of the GlobalPlatform card specification. This client will also allow you to manage the security keys of the card and perform other management operations such as locking the card.

The mainstay solution for this is GlobalPlatformPro, which works well for development purposes with most if not all commonly available cards. If you want to get started right now then this is the tool for you.

JavaCard Simulator
------------------

There exist both proprietary and open-source simulators for JavaCard environments that can be used for development and testing.

