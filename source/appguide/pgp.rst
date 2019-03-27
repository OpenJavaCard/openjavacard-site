OpenPGP Keys
============

Specification
-------------

The basis for using PGP with smart cards is the `OpenPGP card specification <https://g10code.com/p-card.html>`_ published by `g10code <https://g10code.com/>`_.

This specification allows using any compliant smart card with PGP implementations such as `GnuPG <https://gnupg.org/>`_.

If your card has NFC then you can also use it with compliant smartphone applications such as `OpenKeyChain <https://openkeychain.org>`_.

Using smartpgp
--------------

The recent SmartPGP applet supports version 3 of the OpenPGP card specification.

It requires JavaCard 3.0 support from the card.

https://github.com/ANSSI-FR/SmartPGP

Using ykneo-openpgp
-------------------

Another option is using the Yubico OpenPGP applet, which supports version 2 of the OpenPGP card specification.

It can run on pretty much any modern JavaCard but will be limited to 2048 bit RSA keys.

https://github.com/Yubico/ykneo-openpgp

