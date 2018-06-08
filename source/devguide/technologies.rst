Technologies
============

ISO7816
-------

Contact-based smartcards have been around since the 1980s, and today most of us will own several.

These cards are mostly built to standards from the ISO 7816 series, which defines the physical, electrical and protocol characteristics of these cards. It also specifies several frameworks for applications involving cryptography and data storage.

Cards have supported multiple applications for a long time, and so the ISO specifications also specify applet naming using binary AIDs as well as a global registry infrastructure with both an international registry and various national registries.

Today smartcards are also integrated as components in devices with different form factors such as USB tokens, microSD cards, NFC devices and mobile phones. These form factors have considerable influence on how the cards are used, but the technology remains essentially the same.

JavaCard
--------

Since the 1990s an increasing number of smartcards are based on JavaCard, a technology to run Java on smartcards developed by Sun Microsystems and others. The relevant specifications and corresponding development tools are now maintained by Oracle.

These specifications define a Java runtime and machine environment as well as some basic library packages, a considerable portion of which are optional. There are two feature variants of JavaCard, called Classic and Connected. The Connected variety includes advanced technologies such as HTTP support and is not widely available.

Several specification versions exist. As of 2018 most newer cards support JavaCard 3.0, while previously cards implementing JavaCard 2.1 and 2.2 where most common.

The specifications include a domain-separation security model as well as sharing of objects between applets, allowing advanced architectures to be implemented.

Loading and management of applets and packages on actual cards is not specified in JavaCard. The GlobalPlatform card standards fill in this gap.

GlobalPlatform
--------------

The GlobalPlatform organization is an industry association between various companies that maintains a series of standards on security systems. These standards are related to EMV payment, ETSI mobile communications, TCG trusted computing and various other security technologies.

Of specific interest here are the GlobalPlatform card specifications, which specify a set of protocols for loading and managing applets on smartcards. The specifications include a series of secure channel protocols (SCP) and build on the domain-separation model specified in JavaCard.

Using a GlobalPlatform client and the required security keys one can load applications onto a card, create security domains and perform various other operations for key and identity management.

The specifications also define a Java package for common card services. It provides access to GlobalPlatform state, an API for integrating the cards SCP into an application and finally a mechanism for card-global authentication mechanisms.

NFC
---

Near-Field Communications (NFC) allows contactless communication between various forms of devices, including smartcards in both card and token form.

SIM Toolkit
-----------

The SIM Toolkit standard allows the development of JavaCard applications specifically for SIM cards.
