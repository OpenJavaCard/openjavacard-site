Technologies
============

JavaCard
--------

Since the 1990s an increasing number of smart cards and other security elements are based on JavaCard, a technology to run Java on very small systems, developed by Sun Microsystems and others. The relevant specifications and corresponding development tools are now maintained by Oracle.

These specifications define a Java runtime and machine environment as well as some basic library packages, a considerable portion of which are optional. There are two feature variants of JavaCard, called Classic and Connected. The Connected variety includes advanced technologies such as HTTP support and is not widely available.

Most security elements are based on small microcontrollers and are therefore very limited in resources. Most devices - even in 2019 - use enhanced 8/16-bit microcontrollers and have only a few 100 kBytes of persistent memory in addition to a few kBytes of RAM.

The Java environment available on the platform can hardly be compared to traditional Java on desktops or even embedded platforms such as J2ME.

.. table:: Comparison of JavaCard and JavaSE
   :widths: auto

   ==========  =========================================  ========================================
   Feature     JavaCard                                   JavaSE
   ==========  =========================================  ========================================
   Memory      ~100 kB persistent. ~4 kB transient.       Megabytes. Gigabytes.
   GC          Explicit only. Support optional.           Generally available.
   Types       No float or double. No 32-bit int.         All types available.
   Arrays      One dimension. Only scalars and Object.    Many dimensions. Any type.
   Strings     No support at all.                         Always available.
   Library     Limited. Microcontroller-like.             Huge.
   Objects     Always persistent. Considered expensive.   Unrestricted use.
   ==========  =========================================  ========================================

Several specification versions exist. As of 2019 most newer cards support JavaCard 3.0, while previously cards implementing JavaCard 2.2 where most common. The main difference is in the set of supported ciphers.

.. table:: Versions of the JavaCard specification
   :widths: auto

   =======  ========
   Version  Released
   =======  ========
   3.0.5    2015
   3.0.4    2011
   3.0.3
   3.0.2
   3.0.1    2009
   2.2.2    2006
   2.2.1    2003
   2.2      2002
   2.1.1    2000
   2.1      1999
   =======  ========


The specifications include a domain-separation security model as well as sharing of objects between applets, allowing advanced architectures to be implemented.

Loading and management of applets and packages on actual cards is not specified as part of the platform, which only provides some base abstractions. Real-world cards exclusively implement the GlobalPlatform framework for card management.

GlobalPlatform
--------------

The GlobalPlatform organization is an industry association between various companies that maintains a series of standards on security systems. These standards are related to EMV payment, ETSI mobile communications, TCG trusted computing and various other security technologies.

Of specific interest here are the GlobalPlatform card specifications, which define a set of protocols for loading and managing applets on smartcards based on the earlier VISA OpenPlatform specification. The specifications also describe several secure channel protocols (SCP) and on-card APIs.

Using a GlobalPlatform client and the required security keys one can load applications onto a card, create security domains and perform various other card and application management operations.

Applications running on a card can use GlobalPlatform APIs to use the cards secure channel implementation, change the state of the card and other applications, access services from other applications, change the ATR of the card etc.

The GlobalPlatform specification has undergone significant evolution and has expanded into a set of specifications over time. Some functionality is specified in separately-versioned amendments. The following table provides an overview over the various versions.

.. table:: Versions of the GlobalPlatform card specification
   :widths: auto

   ========= ============= ======================================================================= ====== ======= =======
   Version   Released      Features                                                                GP API CL API  UP API
   ========= ============= ======================================================================= ====== ======= =======
   2.3.1     March 2018    SCP02 deprecated                                                        1.6    1.2/1.3 1.0/1.1
   2.3       October 2015  Introduction of software upgrade mechanism                              1.6    1.2/1.3 1.0/1.1
   2.2.1     January 2011  Introduction of confidential card content management                    1.5    1.1/1.2
   2.2+C     February 2010 New amendment C: Contactless services and API                           1.4    1.0
   2.2+B     June 2009     New amendment B: Application management via HTTP                        1.3
   2.2+A     January 2009  New amendment A: Errata and precisions                                  1.2
   2.2       March 2006    Applet personalization, Feature lockdown, Install-time memory limits    1.1
   2.1.1     March 2003    Logical channels, Improved SCP cryptography                             1.0
   2.1       June 2001     GP API, GP version recognition, ExM listing in registry                 1.0
   2.0.1     April 2000    Uses the old VISA OpenPlatform on-card API                        
   ========= ============= ======================================================================= ====== ======= =======

The specification defines several secure channel protocols intended allow secure card management. Most cards use the old and somewhat problematic SCP02 protocol based on 3DES. More modern cards use SCP03 by default. Asymmetric secure channel protocols are theoretically available but cannot be used in most cases because reconfiguring to a different protocol is a proprietary operation.

In many cases you will have to live with SCP02, which has weaknesses such as possible plaintext recovery and cipher malleability issues because of its use of the Encrypt-and-MAC scheme. Using this protocol over unsecured channels is not recommended, but it should still provide security in systems where SCP02 is relied on only for authorization in protected environments. Modern cards using SCP03 are secure enough to perform in-field management through the secure channel.

.. table:: Variants of the GlobalPlatform secure channel protocol
   :widths: auto

   ======== ============ ======================================================================= =============== ============================
   Protocol Ciphers      Features                                                                Security        Availability
   ======== ============ ======================================================================= =============== ============================
   SCP01    DES          Command authentication and encryption                                   Insecure         Obsolete
   SCP02    3DES         Command auth and optional enc, optional response auth                   Problematic      Common
   SCP03    AES-128      Command auth and optional enc, optional response auth and enc           Okay             Some cards only
   SCP10    RSA, ECC
   ======== ============ ======================================================================= =============== ============================

Several on-card APIs are defined in various parts of the specification. As other JavaCard APIs these are versioned, with the versions roughly corresponding to specification revisions.

The org.globalplatform main API (and its predecessor com.visa.openplatform) is available on most cards, providing a range of security and management functionality. Applications can use the secure channel implementation and keys of their hosting security domain. They can also - if permitted - manage the state of the card and applets by changing their lifecycle state. There also is a mechanism for accessing services from other applets on the same card. And there also is a method for changing the so-called historical bytes of the ATR, which are used in card and application detection.

Starting with GlobalPlatform 2.2, contactless cards can implement the optional org.globalplatform.contactless API, allowing permitted apps low-level access to the NFC interface. Through this mechanism it is possible to implement NFC protocols that are not based on ISO7816 APDUs. Cards with this feature can also offer a so-called Contactless Registry Service (CRS) to enforce NFC communication policy.

Starting with GlobalPlatform 2.3, software upgrades with data migration have been standardized. Data migration is performed using the org.globalplatform.upgrade API.

.. table:: APIs specifified in GlobalPlatform specifications
   :widths: auto

   ============================== ======================================================================= ====================
   Package                        Purpose                                                                 Availability
   ============================== ======================================================================= ====================
   com.visa.openplatform          Obsolete predecessor of org.globalplatform                              Legacy cards
   org.globalplatform             Card and application management                                         Commonly available
   org.globalplatform.contactless Management of contactless interfaces and contactless application access
   org.globalplatform.upgrade     Facilitating code upgrade with data preservation
   ============================== ======================================================================= ====================

NFC
---

Near-Field Communications (NFC) allows contactless communication between various forms of devices, including smartcards in both card and token form. This communication can either be in the form of smartcard commands or by using or emulating an NFC memory device, which are actually based on a small set of tightly specified smartcard commands. The memory variant is used for what is commonly called an "NFC Tag", which will contain a so-called NDEF record. These records can contain simple data objects such as strings, URLs and vCard records.

In the JavaCard world NFC is just another interface to the smartcard. It uses the same protocols as contact-based interfaces. The main practical difference is that the card only remains powered for a short time. A smartcard application can determine what interface a command came from and enact appropriate policy to balance out the ad-hoc nature of NFC card usage.

It is possible to emulate an NFC memory device on a smartcard, allowing for the transfer of NDEF records. Some smartcards include additional hardware to facilitate doing so, but this is generally not required unless you need to be compatible to proprietary NFC security technologies such as Mifare.

NFC is not limited to phone-and-card and card-and-terminal applications. There are large-scale applications of NFC where the phone actually acts as an NFC command target (mobile-phone payment). Other applications use stationary devices that act as an NFC target so that the interaction is between a phone and a stationary object - possibly using online transactions (used in the travel industry for tracking-based fare solutions).

SIM Toolkit
-----------

The SIM Application Toolkit (commonly called SIM Toolkit or STK) standard allows the development of JavaCard applications specifically for SIM cards, allowing the development of card applications providing value-added services and provider services integration.

STK applications can provide interactive text-oriented menus that will be displayed by the phone. They can also implement USSD dialing codes. It is also possible to expose SIM applications to applications on the host phone. All of this is done through STK-specific JavaCard APIs and SIM-specific smartcard commands.

In practice, this technology is only available to mobile phone network operators and their subcontractors. This does, however, include operators of open-source GSM networks.


.. _iso7816:

ISO 7816
--------

Contact-based smartcards have been around since the 1980s, and today most of us will own several.

These cards are mostly built to standards from the ISO 7816 series, which defines the physical, electrical and protocol characteristics of these cards. It also specifies several frameworks for applications involving cryptography and data storage, which many applications use as a definition basis.

Cards have supported multiple applications for a long time, and so the ISO specifications specify applet naming using binary AIDs as well as a global registry infrastructure with both an international registry and various national registries. As of 2018 most of these registries seem to be quite obscure. See :ref:`aid-registries`.

Today smartcards are also integrated as components in devices with different form factors such as USB tokens, microSD cards, NFC devices and mobile phones. These form factors have considerable influence on how the cards are used, but the technology remains essentially the same.

.. table:: Standards in the ISO 7816 series
   :widths: auto

   ===========  =======================================================================  ==================
   Standard     Title                                                                    Relevance
   ===========  =======================================================================  ==================
   ISO 7816-1   Cards with contacts - Physical characteristics                           Card production
   ISO 7816-2   Cards with contacts - Dimensions and location of the contacts            Card production
   ISO 7816-3   Cards with contacts - Electrical interface and transmission protocols    Card production
   ISO 7816-4   Organization, security and commands for interchange                      App development
   ISO 7816-5   Registration of application providers                                    App development
   ISO 7816-6   Interindustry data elements for interchange                              App development
   ISO 7816-7   Interindustry commands for Structured Card Query Language (SCQL)         Rare
   ISO 7816-8   Commands and mechanisms for security operations                          PKI apps
   ISO 7816-9   Commands for card management                                             GlobalPlatform
   ISO 7816-10  Electronic signals and answer to reset for synchronous cards             Card production
   ISO 7816-11  Personal verification through biometric methods                          Rare
   ISO 7816-12  Cards with contacts - USB electrical interface and operating procedures  Card production
   ISO 7816-13  Commands for application management in a multi-application environment   GlobalPlatform
   ISO 7816-15  Cryptographic information application                                    Crypto apps
   ===========  =======================================================================  ==================

