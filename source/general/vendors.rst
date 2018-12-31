Vendor Relations
================

We want to work with smart card vendors to promote and advance the cause of open-source software on the JavaCard platform. By lowering the barrier of entry, an open-source approach can open new market opportunities and enable community-driven innovation.

In times of increasing fear of security issues we see an opportunity for card vendors to establish new markets based on open-source and startup-developed security products. Both communities share the need for increased openness from vendors to expedite the development process.

There are also opportunities lurking in an open-source approach to card applications. Open-source application solutions, if properly executed and marketed, can significantly reduce application development cost and complexity - both being important issues for startups and open-source projects. Many opportunities in smartphone applications have already been missed because of a lack in effective JavaCard market strategies.

Opening Up
----------

Many applications of interest to the open-source community are hampered by the lack of very specific bits of information, some of which might be readily releasable once identified. This is an attempt of collecting the most promising ones.

* Access to RSA beyond 2048 bits

  * Most cards are limited to 2048 bits in the public API
  * Some regulatory agencies are recommending 4096 bits
  * Performance is an issue, but not a showstopper
  * An API wrapper could provide a short-term solution
  * Open-source market does not tolerate obsolete ciphers

* Availability of BigInteger support

  * Most cards are not shipped with BigInteger support
  * Open-source market wants to use custom EC curves
  * Uses for on-card Diffie-Hellman have been proposed

* Improve availability of advanced secure messaging

  * Most low-volume cards are still shipped with SCP02 using 3DES
  * Even cards with AES support do not support SCP03
  * Vendors should negotiate newer protocols as default with resellers
  * Open-source market does not tolerate obsolete ciphers

