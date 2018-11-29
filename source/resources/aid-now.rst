AID Now!
========

Do you want to publish your open-source JavaCard application with a proper AID?

Are you tired of filling out paper forms and paying money to allocate a RID from some government agency?

Tire no more! AID assignment has entered the 21st century with our self-assignment program "AID Now!".

Using Tools
-----------

The :ref:`OpenJavaCard Tools <project-tools>` package contains a command for generating AIDs.

Stay tuned for full documentation.

Self-Assignment
---------------

We are working with a partner to establish AID registries that are better suited to open-source use than the traditional ISO-specified registry hierarchy. Our partner has kindly allowed use of a part of their AID space for self-assignment.

An AID is up to 16 bytes long, with 5 bytes being used for the RID. In our assignment scheme, another byte is required to discriminate between assignment types. This leaves 10 bytes, of which 8 are pseudo-randomly assigned. This leaves 2 bytes for version selection and other subdivisions while providing collision resistance of 8 times 2^64. We believe that this is sufficient for open-source use.

.. table:: Allocations for AID self-assignment
   :widths: auto

   =============  ==========================================
   AID prefix     Name
   =============  ==========================================
   D276000177E0   Self-Assigned Experimental Applications
   D276000177E1   Self-Assigned Experimental Packages
   D276000177E2   Self-Assigned Experimental Libraries
   D276000177E3   Self-Assigned Experimental Domains
   D276000177F0   Self-Assigned Production Applications
   D276000177F1   Self-Assigned Production Packages
   D276000177F2   Self-Assigned Production Libraries
   D276000177F3   Self-Assigned Production Domains
   =============  ==========================================

Justification
-------------

Allowing self-assignment might seem like a standards violation to some parties because the application vendor is not actually registered. In practice it is already common practice to use AIDs allocated to other organizations, and there is no rule disallowing a self-assignment system such as ours.

The GlobalPlatform card specification uses an AID assigned to VISA. The NDEF Type 4 standard by the NFC Forum uses an AID assigned to NXP Germany. Really we are doing exactly what others are doing. The only difference is that we are doing it openly.

