# Proposal 00001: Drone Certificate Management

The best current practice for securitisation at the RPAS level is the Public Key Infrastructure. While this works in principle, several use-cases such as de-authorisation of individual RPASs fit the X.509 certification scheme in very standard ways. The usability of PKI will remain essential to the functionality that the manufacturer must provide RPAS operators, however the adoption of a X.509 architecture is recommended as a future-proof solution, and is being actively considered as an option for inclusion in this standardisation.

In such an architecture, in addition to each RPAS manufacturer being issued X.509 security certificates by a valid Certificate Authority, each Digital Sky Service Provider and RPAS must also be issued similar security certificates. In comparison with the current best practice, the additional burden of certificate management would be shared by the DSP, UFII and the Certifying Authorities in question. This architecture would also make each RPAS compliant with the Information Technology Act as per Section 1.4.7. It is also recommended that all data to be transmitted to an external system by the RPAS hardware be signed using the Keystore corresponding to the issued X.509 security certificate.

The proposed distribution of responsibilities by entity to ensure a secure architecture is as follows.

## Digital Sky Service Provider (e.g. Digital Sky, etc.)

  Coordinating between all other entities for
  
  1. KYC
  1. Certificate issuance
  1. Certificate revocation & rotation
      1. Receipt of of Rotation/Revocation requests
      1. Forwarding approved Rotation/Revocation requests to Certifying Authority
      1. RPAS registration, deregistration, flight log submission, etc. 

## Certifying Authority (e.g. e-Mudhra, etc.)
1. KYC
1. Maintenance of KYC data for issued Certificates
1. Maintenance of Certificate Revocation List

##  Law Enforcement (e.g. Police, Governing bodies)
1. Communication of FIR reports, etc. for certificate rotation/revocation requests
  
  Law enforcement can ideally ask CA to revoke a 1. certificate.

## UFII

  Approval of
  1. RPAS Registration
  1. RPAS Deregistration
  1. RPAS Flight Log submission
  1. Mission Plans (captured as a Flight Permit)
  1. Certificate Rotation/Revocation requests

As a mandatory security check for each communication between any of the above entities, the aforementioned must implement standard X.509 certificate validation and check Certificate Revocation Lists (or implement OCSP).

A supplementary proposal is also under consideration where Certifying Authorities, such as e-Mudhra, must create a Sub-Certifying Authority for DGCA which would be the default Certifying Authority for all RPAS, RPAS Manufacturer and Digital Sky Service Provider certificates.
