Naming
======

Java Packages
-------------

As with any other Java-based platform, code is organized using the hierarchical package namespace. It is good practice to use an internet domain controlled by you as the base for your package namespace.

In JavaCard packages also provide the granularity at which software can be installed. A JavaCard package directly corresponds to a Java package, which is given an additional name in the form of an AID.

If you want to share code between packages, for example in a library, you will have to maintain a namespace of package names and corresponding AIDs, all of which should be unique within the respective scope. It is recommended that you use a properly formed AID as detailed below.

.. _aid-naming:

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

.. _aid-structure:

AID Structure
-------------

The namespace for these AIDs is specified and maintained by ISO. Assignment happens in the form of 5-byte RIDs (registry identifiers). Registries exist on a national level as well as internationally within ISO. To obtain a registration you will generally have to go through your national registry, which normally should be your national ISO member organization. Various countries have delegated registry duties to other organizations, so it can be hard to find out who is responsible.

The RID can be combined with a so-called PIX, defined by the registrant, to form a complete AID. It is the responsibility of the registrant to define a future-proof assignment scheme for AIDs. A reasonable practice is to divide the available 11-byte PIX space, first by purpose and then by application. The remaining PIX can be used for protocol versioning and serial numbers, allowing several independent and isolated instances of the same application to exist on the same card by having different serial number suffixes.

There are different prefixes for RIDs assigned by ISO (starting with 0xA) and national registries (starting with 0xD). International RIDs are assigned sequentially by ???. National RIDs indicate the country using the ISO-3166 3-digit country code in BCD form after the 0xD prefix. For example, Denmark has the 3-digit code 208 and uses the prefix 0xD208, while Germany uses prefix 0xD276 corresponding to code 276. Note that the assigned RID is 5 bytes long in both cases.

=========================== =====================
RID                         PIX
=========================== =====================
5 bytes                     0-11 bytes
Assigned by registry        Managed by registrant
Axxx = International
Dccc = National
=========================== =====================

.. _aid-registries:

AID Registries
--------------

Assignment of AIDs is performed by a global hierarchy of registries defined by :ref:`iso7816` standards. Each ISO member nation is supposed to operate a registry under the authority of its respective ISO member organization. Most of these registries seem to be obscure and we have yet to find a useful list.

.. table:: List of known official RID registries
   :widths: auto

   ====== ======= ========= ============== ==================== ================= =========================================
   Prefix Country Authority Registry       Process              Fee               Website
   ====== ======= ========= ============== ==================== ================= =========================================
   D276   Germany DIN e.V.  Fraunhofer SIT Paper                €100 excl. VAT    https://www.kartenbezogene-identifier.de/
   ====== ======= ========= ============== ==================== ================= =========================================

The OpenJavaCard project is pursuing the creation of an AID registry suitable for open-source use in cooperation with a partner. Stay tuned.

Card Identification
-------------------

Some cards support an option for unique card identification that is based on a pair of identifiers called the issuer identification number (IIN) and the card image number (CIN).

Card Lifecycle
--------------

Many (but not all) cards provide a lifecycle record defined by GP (and possibly ISO) called the CPLC (Card Production Life-Cycle).

