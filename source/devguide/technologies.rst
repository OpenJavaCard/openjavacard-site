Technologies
============

ISO7816
-------

Contact-based smartcards have been around since the 1980s, and today most of us will own several.

These cards are mostly built to standards from the ISO 7816 series, which defines the physical, electrical and protocol characteristics of these cards. It also specifies several frameworks for applications involving cryptography and data storage.

Cards have supported multiple applications for a long time, and so the ISO specifications specify applet naming using binary AIDs as well as a global registry infrastructure with both an international registry and various national registries.

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

Near-Field Communications (NFC) allows contactless communication between various forms of devices, including smartcards in both card and token form. This communication can either be in the form of smartcard commands or by using or emulating an NFC memory device, which are actually based on a small set of tightly specified smartcard commands. The memory variant is used for what is commonly called an "NFC Tag", which will contain a so-called NDEF record. These records can contain simple data objects such as strings, URLs and vCard records.

In the JavaCard world NFC is just another interface to the smartcard. It uses the same protocols as contact-based interfaces. The main practical difference is that the card only remains powered for a short time. A smartcard application can determine what interface a command came from and enact appropriate policy to balance out the ad-hoc nature of NFC card usage.

It is possible to emulate an NFC memory device on a smartcard, allowing for the transfer of NDEF records. Some smartcards include additional hardware to facilitate doing so, but this is generally not required unless you need to be compatible to proprietary NFC security technologies such as Mifare.

NFC is not limited to phone-and-card and card-and-terminal applications. There are large-scale applications of NFC where the phone actually acts as an NFC command target (mobile-phone payment). Other applications use stationary devices that act as an NFC target so that the interaction is between a phone and a stationary object - possibly using online transactions (used in the travel industry for tracking-based fare solutions).

SIM Toolkit
-----------

The SIM Application Toolkit (commonly called SIM Toolkit or STK) standard allows the development of JavaCard applications specifically for SIM cards, allowing the development of card applications providing value-added services and provider services integration.

STK applications can provide interactive text-oriented menus that will be displayed by the phone. They can also implement USSD dialing codes. It is also possible to expose SIM applications to applications on the host phone. All of this is done through STK-specific JavaCard APIs and SIM-specific smartcard commands.

In practice, this technology is only available to mobile phone network operators and their subcontractors. This does, however, include operators of open-source GSM networks.
