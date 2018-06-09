Naming
======

Java Packages
-------------

As with any other Java-based platform, code is organized using the hierarchical package namespace.

AID Naming
----------

Smartcards, including JavaCard ones, use so-called AIDs (application identifiers) to identify on-card objects. These identifiers, commonly represented as hexadecimal strings, are binary strings with a length of between 5 and 16 bytes.

There are several types of objects that are referred to by AID:

======= ======================================== =================================================================
Type    Description                              Created
======= ======================================== =================================================================
Applet  Selectable installed applet              by installing a module from a previously loaded package
Domain  On-card security domain                  by installing a special-purpose runtime-provided module
Module  Installable module                       by loading a package that contains module/applet definitions
Package Direct equivalent of a Java package      by loading a CAP file corresponding to the package
======= ======================================== =================================================================

AID Structure
-------------

The namespace for these AIDs is specified and maintained by ISO. Assignment happens in the form of 5-byte RIDs (registry identifiers). Registries exist on a national level as well as internationally within ISO. To obtain a registration you will generally have to go through your national registry, which normally should be your national ISO member organization. Various countries have delegated registry duties to other organizations, so it can be hard to find out who is responsible.

The RID can be combined with a so-called PIX, defined by the registrant, to form a complete AID. It is the responsibility of the registrant to define a future-proof assignment scheme for AIDs. A reasonable practice is to divide the available 11-byte PIX space, first by purpose and then by application. The remaining PIX can be used for protocol versioning and serial numbers, allowing several independent and isolated instances of the same application to exist on the same card by having different serial number suffixes.

This makes for the following basic structure:

=========================== ===================== =====================
Prefix                      Registrant            PIX
=========================== ===================== =====================
2 bytes                     3 bytes               0-11 bytes
Assigned by ISO             Assigned by registry  Managed by registrant
Axxx = ISO, Dxxx = National Sequential assignment
=========================== ===================== =====================

The prefix and the registrant number form the RID. For international registrations the whole 5-byte RID is specified by the ISO registry, including the unspecified bytes in the prefix. For national registries the prefix specifies the ISO 3166-1 country code of the respective country in BCD form. For example Denmark uses D208 while Germany uses D276.

AID Registries
--------------

The following is a list of known official national registries.

======= ========= ============== ================= =========================================
Country Authority Registry       Fee               Website
======= ========= ============== ================= =========================================
Germany DIN e.V.  Fraunhofer SIT EUR 100 excl. VAT https://www.kartenbezogene-identifier.de/
======= ========= ============== ================= =========================================
