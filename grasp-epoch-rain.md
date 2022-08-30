---
title: Distributing fresh Epoch Identifiers using GRASP
abbrev: Epoch Rain
docname: draft-richardson-anima-rats-grasp-epoch-rain-00

stand_alone: true
ipr: trust200902
area: Internet
wg: anima Working Group
kw: Internet-Draft
cat: std

pi:    # can use array (if all yes) or hash here
  toc: yes
  sortrefs:   # defaults to yes
  symrefs: yes

author:

- ins: M. Richardson
  name: Michael Richardson
  org: Sandelman Software Works
  email: mcr+ietf@sandelman.ca
- ins: H. Birkholz
  name: Henk Birkholz
  org: Fraunhofer SIT
  abbrev: Fraunhofer SIT
  email: henk.birkholz@sit.fraunhofer.de
  street: Rheinstrasse 75
  code: '64295'
  city: Darmstadt
  country: Germany
- ins: W. Pan
  name: Wei Pan
  org: Huawei Technologies
  email: william.panwei@huawei.com

venue:
  group: anima
  mail: anima@ietf.org
  github: mcr/grasp-epoch-rain

normative:
  BCP14: RFC8174
  RATSARCH: I-D.ietf-rats-architecture
  RFC8990:
  RFC8994:

informative:
  RFC7030:
  RFC8995:

--- abstract

This document describes a way to distribute Epoch Identifiers using the GRASP protcol.
Epoch Identifiers can be used a source of freshness for signature based systems, such as Remote Attestation.

--- middle

# Introduction

The {{-RATSARCH}} describes a number of ways in which remote attestation systems can assure that they are dealing with fresh evidence.
One such way is via the Epoch Identifier (Epoch ID).
This document describes a way to distribute Epoch Identifiers via GRASP M_FLOOD messages.

The mechanism describe in this document can be used for any digital signature system which is sensitive to replay attacks.

While many session-based systems such as TLS or IPsec {{?RFC4301}} handle replay via an incrementing sequence number (and a replay window to deal with out-of-order delivery), in systems where the communication pattern is many to one, one to many, or adhoc the use of a single counter does not scale well.

## Challenges

Epoch IDs can not be monotonically increasing counters!
Such a thing would be deterministic and allow attackers to trivially guess what the next Epoch ID is.

A key point about Epoch IDs is that they are unpredictable and non-deterministic.
A receiver that observes a particular Epoch ID is therefore sure that any transmitter that is using it (and has included it in a signed object), could not have constructed the signed artifact prior to the Epoch ID having been transmitted.

The Epoch ID distribution must also be secure.
They do not need to be confidential, but receivers must be sure that the Epoch ID comes from the legitimate Epoch distributor.
This implies that Epoch IDs must be signed with a key known to the receivers.

The Epoch ID process must also be immune to replay attacks.
That is, there must be a process that allows receivers to be able to verify that they are fresh.

# Protocol



# Privacy Considerations

YYY

# Security Considerations

ZZZ

# IANA Considerations

# Acknowledgements

Hello.

# Changelog


--- back

