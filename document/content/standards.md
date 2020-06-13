**Digital Sky Technology Standard**

> For questions and feedback on the technology standard, please reach out to [forum.digitalsky.dgca.gov.in](http://forum.digitalsky.dgca.gov.in) or [DSP Working Group](https://groups.google.com/forum/#!forum/drone-dsp)


# Definition of Terms

| Term | Description |
| ---- | ------------|
| CA   | Certifying Authorities |
| DGCA | Directorate General of Civil Aviation |
| DHE | Ephemeral Diffie-Hellman |
| DSC | Digital Signature Certificate |
| DSP | Digital Sky Service Provider |
| ECDHE | Elliptic Curve Diffie-Hellman |
| GLPS | Global Level Positioning System (GPS, GLONASS, Galileo, IRNSS, etc) |
| HSM | Hardware Security Module |
| IST | Indian Standard Time |
| NPNT | No Permission No Takeoff |
| PII | Personally Identifiable Information |
| PKI | Public Key Infrastructure |
| RFM | Registered Flight Module |
| RPAS | Unmanned Aircraft System(s) |
| RPAS | Remotely Piloted Aircraft System(s) |
| UFII | Unified Flight Information Interface |
| UIN | Unique Identification Number |
| UUID | Universally Unique Identifier |

# Version History

| Version | Date       | Comments | 
| ------- | ---------- | -------- |
| 1.0     | 22/10/2018 | Publication of Registered Flight Module v1.0 Technology Standard |
| 1.1     | 27/6/2019  | Revision in Exhibit C Diagram
|         |            | Addition of 2.3 - Communication Requirement for multiple chip or 
|         |            | &nbsp;module design |
|         |            | Addition 3.1 Key Generation |
|         |            | Extension in Keypair Generation to allow for Smart Card/PKI Token
|         |            | &nbsp;in addition to HSM |
|         |            | Revision in Flight Permit from XML to JSON |
|         |            | Removed support for pilot pin |
|         |            | Removed test cases related to pilot pin |
|         |            | Added NPNT test tool |
|         |            | Added support for ECC |
|         |            | Removed Pilot PIN RFM API |
| 1.2     | 11/01/2020 | Moved technical specification of Device Registration and 
|         |            | &nbsp;Deregistration API to UFAMS Github Repo |
|         |            | Rename Permission Artifact to Flight Permit |
|         |            | Moved technical specification of Flight Permit to UFAMS Github 
|         |            | &nbsp;Repo |
|         |            | Moved technical specification of Flight Log Schema and Chaining
|         |            | &nbsp;to UFAMS Repo |
|         |            | Added section 1.4.11 on UFII, DigitalSky Service Providers and 
|         |            | &nbsp;Digital Sky |
|         |            | Update section 7.4 to include information about development of 
|         |            | &nbsp;standards |

# Introduction

Imagine a future where Remotely Piloted Aircraft Systems (RPAS) augment human capabilities. They could help farmers prioritize where to apply fertilizer, or help energy companies monitor their infrastructure, or even enable emergency response teams to quickly map the extent of damage after natural disasters. In the near future, RPAS could deliver packages, streamline agriculture management, reinvent human mobility, and even save lives. Therefore, Digital Sky puts in place a seamless and secure technology and regulatory framework to integrate this new technology into the Indian airspace.

Digital Sky enables a proactive approach to enforcement of safety and security guidelines by ensuring that a RPAS does not take-off without a signed digital flight permit, obtained via the Digital Sky Service Providers, and necessary flight logs and occurrence reports are reported back to the relevant authorities via the DSPs.

We envision a future, when millions of RPAS are flying across the country, without significantly increasing the regulatory burden. Thus, Digital Sky can be extended in the future to carry out autonomous flights, automated RPAS traffic control, air taxis, besides other use-cases.

## Mission

The mission of Digital Sky is to create a completely digital, paperless, and presenceless process, thus fast-forwarding to a future of on-demand seamless permissions for RPAS, operators, and pilots.

## Vision

The vision is to create a digital infrastructure that will support safe, efficient, and secure access to Indian airspace for millions of RPAS.

## Target Audience and Prerequisites

This is a technical document and is targeted primarily at RPAS manufacturers or providers who want to build registered flight modules as per this specification. Civil Aviation Requirements for Operation of RPAS are out of scope of this technical document - they have been made available at [CAR D3X-X1](http://dgca.nic.in/cars/D3X-X1.pdf)

**NOTE:** In this document, the term “Flight Module Provider” is used to refer to a RPAS manufacturer or any agency who has partnership with the manufacturer to manage certification and related software/security aspects of registered flight modules:

- One provider may have many RPAS models

- One provider may have many versions of the Registered Flight Module (RFM)

- One Registered Flight Module (RFM) service may handle many models

The Flight Module Provider should be a legal entity registered in India and is responsible for certification, key management (as per this specification), and any security or other responsibilities set forth by DGCA.

For more details on the Registered Flight Module, you may refer to Section 2.

## Guiding Design Principles

### Safety by Design

Every RPAS should be designed, manufactured, remanufactured, or rebuilt with safe design and manufacturing considerations. Improper design and manufacture can result in hazards to personnel if minimum industry standards are not conformed to on mechanical components, controls, methods of operation, and other required information necessary to ensure safe and proper operating procedures.

### Security By Design

The software and systems must be designed from the ground up to be secure. There must be end-to-end security of data using PKI, DSC, tamper detection, and other security measures like continuous monitoring, hunting, and response.

### Privacy By Design

The following privacy principles must be embedded into the design:

- Proactive not reactive; Preventative not remedial

- Privacy as the default setting

- Visibility and transparency – keep it open

- Respect for privacy of all the stakeholders – keep it ecosystem-centric

### Open Platform and Open Standards Based

The framework should use open technology and legal standards available in the country. It should be agnostic to applications, programming languages, and platforms.

### Universal Identity

The technical framework should leverage universal, authenticable, non-repudiable, and digital identities to allow interoperability across all users (pilot, flight module provider, operator, RPAS, etc) in the system. For example, Aadhaar for Individuals, GSTN for Businesses, etc.

### Ecosystem Driven Approach

An ecosystem approach is necessitated such that the interfaces between the partners (like Digital Sky Service Providers and Application Service Providers) and systems (like Unified Flight Information Interface) are well defined and standardized. Hence, there must exist a technology backbone that would hold together this partner ecosystem.

| **Exhibit A: High-Level Overview of Digital Sky Ecosystem** |
| ----------------------------------------------------------- |
| ![](media/exhibit-a.png) |

### Information Technology Act Compliant

The framework must use digital signatures to guarantee non repudiation (includes identity and integrity) of the access permissions given by/for users in permission flows as well as actions taken by the users. This makes the framework fully legal under the IT Act \[1\].

### Minimalist and Evolutionary Design 

The design of the framework should be simple and minimalistic. It should not present adoption barriers for the ecosystem. The design of the systems should be evolutionarily - their capabilities should be built incrementally while allowing for rapid adoption.

### Ease of Doing Business

The framework should be designed by placing the operator in the centre, thus only adopting approaches that are convenient and easy for doing business.

### Digital Enforceability

The framework should allow operators to set permissions and rights for airspace permission access at a fine-tuned level (for example, the ability to choose a polygon area of airspace at a particular altitude and for a particular date and time) and the same must be enforced digitally through No Permission No Takeoff and generation of verifiable flight telemetry.

### UFII, DigitalSky Service Providers & DigitalSky

#### UFII

The Unified Flight Information Interface is an effort to integrate the airspaces of manned and unmanned aircraft systems at the governmental level under the auspices of the Airports Authority of India (AAI). This interface would coordinate data exchange between various security agencies, the DGCA, the Aeronautical Telecommunication Network, the Aeronautical Fixed Telecommunication Network, the Air Defense Units, etc. The purpose of this integration is to enable air traffic management in a concerted fashion.

The UFII will enable private innovators to provide services for unmanned air traffic management. Such innovators are termed as DigitalSky Service Providers (DSP). DSPs would in their regions of operation coordinate with RPAS manufacturers, operators and the RPAS’s wherever possible to maintain conformance with Civil Aviation Requirements and RPAS Guidance Manual. The UFII would also define the data exchange formats for communication between itself and DSPs and between DSPs for various scenarios to ensure interoperability.

#### DigitalSky Service Providers

While the final decisions for most critical processes such as Flight Plan approval, etc. would rest with the UFII, DSPs would provide a valuable intermediate layer by enabling informed flight planning and operations by assessing risks associated with flight plans, providing terrain, mapping & weather data, providing realtime information about constraints, directives, notifications, non-conformance, active operations, and so forth. They may also provide ancillary services enabling registration for RPAS Manufacturers, Pilots, Operators and RPAS units.

#### DigitalSky

The DigitalSky portal is the DigitalSky Service Provider portal that would be operated by the AAI as a standard bearer for DSPs.

##### Release schedule

The UFII and DigitalSky platforms are currently being developed and are planned to be released in stages by February 2021.

# Registered Flight Modules

## Registered Flight Module (RFM)

Registered Flight Modules specification described in this document provides the following key features:

1.  Non Repudiable Identification of RPAS – every Flight Module has a unique identifier allowing end to end traceability, accountability, traffic management, and forms the foundation for issuance of UIN.

2.  No Permission No Takeoff (NPNT) - every RPAS must obtain a valid flight permit and verify the same before it can arm itself.

3.  Eliminating use of synthetic flight logs - there should be no mechanism for any external system to provide simulated flight logs and get it signed.

It is important to note that it is in Flight Module Provider’s interest to ensure the above items are implemented securely since any compromise on these will result in fraudulent activities signed using the Flight Module Provider key. As per IT Act it is essential for the key owners (Flight Module Provider) to protect the signature key and take responsibility for any compromise.

| **Exhibit B: High-Level Overview of RFM Ecosystem** |
| --------------------------------------------------- |
| ![](media/exhibit-b.png) |

DGCA does not mandate any specific hardware design and Flight Module Providers are expected to innovate appropriate form factors for market use. That being said, minimum mandates related to the security of keystore and key management are being prescribed in this specification.

## Levels of RFM Compliance

### Level 0 Compliance 

The Flight Module security implementation has Level 0 compliance if the signing and encryption is implemented within the software zone at host system level. In this case, management of private keys needs to be addressed carefully to ensure it is protected from access by users or external applications. All device providers should at a minimum obtain level 0 compliance and should not have mechanism to easily obtain the private key or inject fraudulent flight logs.

### Level 1 Compliance 

The Flight Module security implementation has Level 1 compliance if the signing and encryption is implemented within the Trusted Execution Environment (TEE) where host system processes or host system users do not have any mechanism to obtain the private key or inject fraudulent flight logs. In this case, management of private keys needs to be fully within the TEE.

## Registration 

## Generation of Keys 

1.  Key pair is generated at RFM level or generated elsewhere and transported to RFM.

2.  If keypair is not generated at RFM, it should be generated within a zone that has the the same security requirements as RFM and has to be transported to the RFM on a communication channel secured using or equivalent of 128bit symmetric key (minimum).

3.  If key rotation is required, the generated key may be signed using the previous key pair and sent to be updated to DigitalSky.

## Registration of Flight Module

Prior to registration of a flight module, the Flight Module Provider must:

1. Register with Digital Sky and provide the list of certified models.

2. Procure a digital certificate from a valid CA\[2\] in India and get it signed by DGCA. The public key in the certificate would be the Flight Module Provider key and it would be used to sign the Drone ID and flight module public key. Flight Module Providers can have one or more keys and can rotate, revoke their keys via Digital Sky.

For registration of each flight module, the Flight Module Provider must provide for a Flight Module Management Client and Flight Module Management Server. (Key Management for the Management Server may be maintained by an external Technology Service Provider through a valid custodian agreement.)

| **Exhibit C: High Level Sequence Diagram of RPAS, Ground Control Station, Management Client and Server, and Digital Sky** |
| ------------------------------------------------------------------------------------------------------------------------- |
| ![](media/exhibit-c.png)                                                                                                  |

### Functionality of Flight Module Management Client

1. Management client may or may not be packaged with RFM Service as an installable.

2. Management client should implement an "init" method internally to check if flight module is registered, connect to management server, initialize and rotate keys, and check for software upgrades.

3. When running, management client should detect for physical flight module connected and readiness of it. The Management Client reads the RPAS Drone ID during each power-up init() call. Then Management Client checks whether the Drone ID is mapped to any UUID (generated and sent by the server for the first time).

4. If UUID is not available, that means the system is not registered. If the flight module is not registered, it should auto initiate registration.
    
    1. In that case to start the registration process, Management Client will send the Drone ID to Management Server
    
    2. Management Server generates new UUID, sends this back to the Management Client, initiates other work-flows with Digital Sky for the RPAS registration
    
    3. The Drone ID can be composed of serial numbers, internal identifiers, signatures, etc. Flight Module Providers must ensure that this Drone ID does not change during the life of that physical flight module.
    
    4. In addition, to avoid invalid/non-genuine flight modules being registered, a concept of "one-time activation code" could be used to authenticate if the flight module is genuine.
        
        1. Flight Module Providers can send the one-time activation codes to people/entities who procure the flight module.
        
        2. This provides a mechanism to do out of band authentication.
        
        3. Once it is activated, optionally user registration can be done and user authentication may be used for all management services in addition to client software authentication.
    
    5. Registration should include Drone ID (serial number or any other internal ID that is used to recognize physical flight module), host fingerprint, timestamp, flight module keys, and other flight module details for authentication, etc.
    
    6. Flight Module Provider may keep additional attributes/info for their own management and audit purposes.
    
    7. Flight Module Provider should check pre-existence of serial number or other physical unique attributes to ensure the same flight module gets the same flight module code UUID. In the case of new registration, the server generates a new flight module code (UUID) and should be sent back to the client.
    
    8. Flight Module Provider’s Management Server should call Digital Sky Register API to ensure flight module is registered with Digital Sky.
    
    9. After successful registration with Digital Sky, Flight Module Provider’s Management Server should sign the flight module public key and return to client.

5. If a flight module is registered, it should initiate key rotation when necessary.
    
    1. Management service should trigger key rotation under 2 scenarios:
        
        1. based on the trigger from management server during "init" (ideally done at least once a day);
        
        2. based on the manual trigger from management client UI (this is needed only in special conditions where manual key reset needs to be triggered). This trigger should call the same "init" to re-initialize.
    
    2. When the key needs to be rotated, flight module should generate the new key pair, send the public key to the server for signing and updating the management server registry.
    
    3. Private key must be generated and stored securely within keystore.
    
    4. See keystore security section (3.1.5) for details on keystore protection.

6. Management client should check for software upgrades and initiate upgrades.

### Functionality of Flight Module Management Server

1. All management server communication must be via HTTPS (with DHE/ECDHE for perfect forward secrecy).

2. Management server should authenticate management clients and allow registration, key rotation, triggering upgrades, and other necessary management services. See previous section for details.

3. Management server should use a Hardware Security Module (HSM)/Smart Card/PKI Token for key management. The HSM/Smart Card/PKI Token must be compliant with FIPS140-2 Level 3 or FIPS140-2 Level 4.

4. Flight Module database, secret token for authenticating management client, flight module fingerprint, user credentials, etc. should be protected through controlled access, encryption, and other security best practices.

5. Appropriate security mechanisms should be in place to protect HSM/Smart Card/PKI Token and flight module database access.

6. Log files should not contain any sensitive data (like private keys, secret tokens, passwords, PII, etc).

7. Management Server should implement configurable key rotation policies and should be configurable as per DGCA policies.

8. All flight modules should generate an asymmetric key pair within the flight module. This would be the flight module key pair. Every physical instance of the flight module should have its own flight module key pair.

9. Flight Module public key should be signed by one of the Flight Module Provider’s keys. The provider must sign the flight module public key on the Flight Module Provider’s server within the HSM/Smart Card/PKI Token.

10. Flight Module Provider MUST ensure each physical flight module has a unique code (drone id). Maximum length of the code is 50 characters when represented as string. To ensure flight module codes are globally unique it is necessary that Flight Module Provider uses a 128-bit UUID (represented in HEX notation).

11. Note: Flight Module public-private key generation and signing of flight module public key with Flight Module Provider key can be performed at any point of time during flight module’s lifecycle.

### Digital Sky APIs for Registration and Deregistration 

The Flight Module Provider’s "Management Server" should request the Digital Sky Registration API whenever a new flight module needs to be registered. The Flight Module Management frontend to management server interfaces are specific to the Flight Module Provider.

These APIs will be provided by Digital Sky and only certified Flight Module Providers will be able to request the same. This will be made possible using IP Whitelisting and validation of the digital signature and API.

For technical details, refer to [https://github.com/iSPIRT/UFAMS](https://github.com/iSPIRT/UFAMS)

**Payload verification process during Registration or Deregistration:**

1. Digital signature is verified against the drone data in the request, using the digital certificate.

2. Verify if the digital certificate belongs to the manufacturer by matching the organization name of the manufacturer saved against the manufacturer business identifer in the digitalsky system with that of the 'o'(case insensitive) property in the subject of the digital certificate.

3. Validate the digital certificate passed as a part of payload using the certificate chain uploaded during the manufacturer profile creation. Validation fails if either the certificate chain itself is invalid or if the digital certificate is invalid.

### Certificates and Keys Policies

1. Below are the currently supported algorithms for digital signing:
    
    1. SHA256withRSA (2048 bit key)
    
    2. ECDSA with safecurves ([https://safecurves.cr.yp.to](https://safecurves.cr.yp.to))

2. All Flight Module Provider certificates should be procured from a certification authority (CA) as per Indian IT Act. ([http://www.cca.gov.in/cca/?q=licensed\_ca.html](http://www.cca.gov.in/cca/?q=licensed_ca.html))

3. All Flight Module Provider certificates should be class II or class III and X509 v3 compliant.

4. Organization attribute in the certificate’s subject SHOULD match the Flight Module Provider’s name registered with DGCA

### Keystore Security

1. Keystore should be limited with read and write rights only for the user as whom the RFM service runs and no other user accounts should have access to it.

2. Keystore password has to be complex and auto generated. The following list of approaches are possible:
    
    1. A combination of random data, user credentials and flight module identification data -derived key using identities
    
    2. The logic describing how the key is derived using these values has to be obfuscated to avoid any possible security threats.
    
    3. The key derivation logic should be in a compiled native machine dependent code and can not be an Open API.
    
    4. The password should be changed for every key rotation.
    
    5. Use White Box Cryptography to derive the password.
    
    6. The password should be more than 16 characters in length and should contain small letters, capital letters, special characters, and numbers.
    
    7. A server side logic to help with opening the keystore.

3. The RFM service should fail its integrity check upon the keystore permissions not correct or has unwanted access and should inform the server about such failures. This failure would be tracked as an incident by the Flight Module Provider.

4. All type of access and access attempts to the keystore should have audit logs.

5. The private key should not be extractable (wrapped or direct)

6. It is recommended that key pair is generated inside the flight module service. Note that flight module authentication must be performed before allowing any connection to management server

7. The keystore has to be cleared and zeroed in case the RFM service is deleted.

For detailed recommendations and best practices on key management, you may refer to the following global standards by NIST:

- Part 1: General: [NIST Publication 800-57 part 1 rev 4](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-4/final)
- Part 2: Best Practices for Key Management Organization: [NIST Publication 800-57 part 2](https://csrc.nist.gov/publications/detail/sp/800-57-part-2/final)
- Part 3: Application-Specific Key Management Guidance: [NIST Publication 800-57 part 3 rev 1](https://csrc.nist.gov/publications/detail/sp/800-57-part-3/rev-1/final)

## Issuance of UIN

Once the flight module has been successfully registered with Digital Sky based on the process outlined in 3.1, following steps need to be completed to receive a UIN:

  - Approve Operator Linkage Request (linking drone with operator)

  - Fill UIN Form on Digital Sky and Submit

  - If approved, then UIN is issued and the flight module is added to the registry.

**Through Digital Sky, an end to end linkage of the Flight Module Provider, RFM/RPAS, Owner, Operator, and Pilot is formed providing traceability and ensuring accountability.**

# Registered Flight Module (RFM) APIs 

The RFM should be implemented at the Flight Controller Level. The RPAS RFM Provider should not allow unnotified access to the UA flight controls - the RFM service should be notified of every call (pertaining to conditions specified in this RFM specification) to the UA flight controller. There should not be any bypassed or unchecked access to the RPAS flight controls.

The flight permits and the flight logs must not be stored by the RFM. It must be stateless and must provide a tamper-proof mechanism to offload any storage and state handling to the host system.

## RFM Core Functionality

### RPAS Identification (Drone ID)

1. Items to be Uniquely Identified to avoid alterations:
    
    1. UID of Hardware modules used like MicroProcessor/Controller, Radio Modules.
    
    2. Version Hash of firmware and bootloader onboard.
    
    3. Unique License/Identifier of Flight Module Provider

2. Layers for Identification:
    
    1. Flight Application: Connected Hardware modules identification, Flight Module Provider License Verification
    
    2. Co-Computer/GCS: Flight Module Provider License Verification.

### Verifying authenticity of the Flight Permit 

Flight Permit is an electronic representation of a permission to fly granted through the Digital Sky Service Providers. For technical specification of flight permit, refer to [https://github.com/iSPIRT/UFAMS](https://github.com/iSPIRT/UFAMS)

The flight permits will come with a digital signature (a form of Public key cryptography), encrypted using Digital Sky private encryption key. The RFM service must use the corresponding public keys (released by Digital Sky) to verify that the flight permit is released by authorised DSP and has not been tampered with during transport.  
If the public key has to be changed (When Digital sky requests the Flight Module Providers to change), the Flight Module Provider has to release a firmware update to update the key. Flight Module Provider should build security measures to ensure that any 3rd party is not able to alter the public keys used to verify the flight permit in the library.

### Provide information of Time and Location bound restrictions to Flight Controller 

The verified flight permit will provide geofence information in horizontal and vertical plane to the Flight Controller. The flight permit also consists of the time period for which the permission is valid.

### Collect Flight Logs

The Flight Module Provider is required to implement functionality to provide following data to the RFM service. This data will be saved against each flight permit.

1. Date-time information from GLPS data in IST

2. Date-time information from system in case GLPS fixture is unavailable.

3. System clock timestamp

4. For each power cycle, the list of takeoff, land coordinates.

5. Upon breach of the geofence, the start/stop timestamp, a list of GLPS coordinates during the time the drone was outside the geofence, captured at 1 Hz minimum.

6. Upon breach of the time limits, the additional time, and list of start/end timestamp for which the RPAS was in air should be provided to the library.

7. The flight logs captured during the period of the flight permit should be stored on the flight controller along with hash of the logs to ensure tamper-proof records. A record must be maintained onboard to connect next and previous flight logs to avoid omission and the same should be inaccessible to the user. Once the flight permit is expired or when user wants to submit logs, the complete bundle of such logs should be signed using RFM private key and submitted to the DSP.

### Sending Flight Logs to Digital Sky Service Provider

The Flight Module Provider is responsible for providing the communication interface between RFM and DSPs or external applications, which can ultimately interact with DSPs. Since, third party applications can provide the functionality for sharing flight permit and flight log data between DSPs and RFM, it is suggested to provide a standardized communication interface to the external applications to interact with RFM’s flight permit and Flight Log APIs. Finally, the Flight Module Provider is responsible for providing to the user, at least one way of sharing this data, either over a direct link between RFM and DSP or through an external application (e.g. Ground Control Station). The technical specification of the flight log is available here: [https://github.com/iSPIRT/UFAMS](https://github.com/iSPIRT/UFAMS)

#### Flight Log chaining

Logs submitted to a DSP must be numbered in an autoincrement fashion starting with 0 (when initialised by a RFM Provider). The last submitted sequence number must be persisted for future submissions. An incident report must be filed with a DSP in case a Log is skipped for any reason. For details, refer to this [standard document](https://github.com/iSPIRT/UFAMS/tree/master/standards/00001-flight-log-chaining.md).

### Reference system for GLPS data

#### Data provided by DSPs

During the exchange of geoposition and altitude data between RFM or GCS and DSPs the reference system that must be used for data being provided by DSPs is the World Geodetic System (WGS84), which uses an ellipsoidal coordinate system for both horizontal and vertical datum. The altitude constraints in a FlightPermit is a typical example of usage of this system.

#### Data provided to DSPs

RFM and GCS reporting such data to DSPs may choose to use the recommended WGS84 system, although this is not mandated. Most commercial GPS units use this system of reference for absolute measurements. In cases where alternate reference systems are used for reported data, DSPs who opt to accept such systems will need to perform appropriate conversions where possible before communication to UFII. The log entries in a FlightLog are a typical example where it is recommended that altitude and geoposition be provided as absolute measurements using WGS84-compatible GPS data.

#### Flight Permits and Altitude Constraints

When a mission plan is filed with a DSP by an operator or pilot, the DSP will be required to apply appropriate altitude constraints for the mission plan based on Digital Elevation Model data, such as SRTM. The altitude constraint will typically take the form of a maximum absolute allowable altitude (WGS84), which would be 100-400ft (operation volume height) above the average land elevation for the region of operation. The operation volume height would vary based on the particulars of the mission. The maximum allowable altitude will be embedded in the FlightPermit for missions approved by UFII.

## RFM API Reference

1. Get\_rfmInfo  
   Parameter 1: IST date-time (fetched from GLPS data or any other source)  
   Output 1: RFM public key  
   Output 2: Digital Sky Public Key being used in RFM  
   Output 3: Firmware Version  
   Output 4: RFM version  
   Output 5: RPAS category  
   Output 6: Operator ID obtained during registration  
   \[Provide RPAS info\]
    
    1. The API will return the required information for any external application.
    
    2. The RFM Provider has to sign the information using RFM private key.

2. Apply Flight Permit:  
   Parameter 1: Flight\_Permit  
   Parameter 2: IST date-time (fetched from GLPS data or any other source)  
   \[ provide flight permit to the RFM \]
    
    1. This API should be called by Flight Controller or host system every time the RPAS is powered on.
    
    2. RFM will verify the signed flight permit using the Digital Sky Public Key.
    
    3. RFM, being stateless, will not store the flight permits in the memory, so Flight Module Provider is responsible for providing relevant flight permit to the RFM on every power cycle. The permission state is maintained by the RFM for the current power session only.
    
    4. RFM will use timestamp provided by Flight Module Provider, the flight permit publish timestamp (marked by DSP when the flight permit is created), and the ttl (time to live) value to validate that the flight permit is eligible at that time and that the system time-date is not falsified.

3. Get\_Geofence\_restriction:  
   Parameter 1: IST date-time  
   \[ provides geofence information to the Flight Controller or Host system after a valid flight permit has been applied \]
    
    1. RFM will verify the date-time stamp to reassert the time validity of the flight permit
    
    2. This API is provided by RFM for the Flight Controller or Host system. The Flight Controller is expected to use this data for enforcing safety restrictions or warning the pilot.
    
    3. It is the responsibility of Flight Module Provider to ensure that the RPAS follows the geofence restrictions. In case of geofence or time limit violations, the Flight Module Provider should provide the event details to the RFM.

4. Get\_time\_restriction:  
   Parameter 1: IST date-time  
   \[ Provides allowed time limit after a valid flight permit has been applied \]
    
    1. RFM will verify the date-time stamp to reassert the time validity of the flight permit.
    
    2. It is the responsibility of Flight Module Provider to ensure that the RPAS is landed before the permitted time period expires. In case of time limit violations, the Flight Module Provider should provide the event details to the RFM

5. Log\_takeoff\_location:  
   Parameter1: IST date-time  
   Parameter2: GLPS coordinates  
   \[ To provide takeoff event information to library for internal logging.\]
    
    1. The Flight Module Provider is responsible to implement the functionality to ensure that this API is called immediately after takeoff event..
    
    2. The Flight Module Provider should not provide any means to bypass the notification to RFM on a takeoff event.
    
    3. The RFM will store and package all such events in one flight log against a flight permit.

6. Log\_Land\_location:  
   Parameter1: IST date-time  
   Parameter2: GLPS coordinates  
   \[ To provide land event information to RFM for internal logging.\]
    
    1. The Flight Module Provider is responsible to implement the functionality to ensure that this API is called immediately after land event.
    
    2. The Flight Module Provider should not provide any means to bypass the notification to RFM on a land event.
    
    3. The RFM will store and package all such events in one flight log against a flight permit.

7. Log\_geofence\_breach:  
   Parameter1: IST date-time  
   Parameter2: Breach\_start\_timestamp  
   Parameter3: Breach\_stop\_timestamp  
   Parameter2: GLPS coordinates  
   \[ To provide geofence breach event information to RFM for internal logging.\]
    
    1. The Flight Module Provider is responsible to implement the functionality to ensure that this API is called immediately after a geofence breach incidence.
    
    2. The Flight Module Provider is responsible for implementing functionality to call this API at 1 Hz, from the time when Geofence is breached to when the drone lands.
    
    3. The RFM will store and package all such events in one flight log against a flight permit.

8. Log\_timelimit\_breach:  
   Parameter1: IST date-time  
   Parameter2: time\_overrun\_start\_timestamp  
   Parameter3: time\_overrun\_land\_timestamp  
   \[ To provide time limit breach event information to RFM for internal logging.\]
    
    1. The Flight Module Provider is responsible to implement the functionality to ensure that this API is called immediately for a time limit overrun event.
    
    2. During the first call, when the drone is still in flight, the time\_overrun\_timestamp parameter will not have any value. The event would be logged as start of time overrun.
    
    3. When the drone lands this API should be called again to indicate end of flight. In this case the API caller needs to provide time\_overrun\_start\_timestamp again. This event will be registered as end of time-overrun event.
    
    4. The RFM will store and package all such events in flight log against a flight permit.

9. Get\_individual\_flight\_logs:  
   Parameter1: IST date-time  
   \[ To get the individual flight logs from the RFM for storage \]
    
    1. The RFM must prepare a flight log after each land, geofence breach, or flight time overrun.
    
    2. These flight logs will be digitally signed by the RFM to make sure that flight logs are not tampered with during the transport. It is Flight Module Provider's responsibility to implement the functionality required to keep the private key secure. These reports may be verified against that public key that was shared during registration of the RPAS.
    
    3. It is the responsibility of the Flight Module Provider to implement the functionality to collect these reports immediately after every takeoff, land, Geofence and time-limit breach event from RFM. In case of crash where such events were not registered, the RFM on next power cycle, should close the log with failed landing incidence.
    
    4. The Flight Module Provider is responsible to implement the functionality to store all the flight logs until they are uploaded to the DSP. This storage should provide the ‘write access’ only to the applications authorized by Flight Module Provider. The read access to the storage should be available in case of accidents. The Flight Module Provider is required to provide the authorities with the specialized equipment required to read the flight logs from a crashed/damaged RPAS’s onboard storage.
    
    5. Flight Module Provider is responsible to provide communication interface to upload the flight log directly to the DSP or through external applications, such as Ground Control Station.
    
    6. The Flight Module Provider is responsible to ensure the storage space for logs. If storage space is not available for logging then the flight should not be allowed.

10. Bundle\_flight\_logs:  
   Parameter1: IST time-stamp  
   Parameter2: List\_of\_individual\_incidence\_reports\_from\_storage  
   Parameter3: Flight Permit  
   Output1: Bundled\_incident\_report\_with\_digital signature.  
   \[ to bundle the signed flight logs from storage into a single bundle (a bundle per flight permit). \]
    
    1. After the time-period of a flight permit is over, the user has to submit the flight logs to Digital Sky APIs within 3 days. The Flight Module Provider is required to implement the functionality to provide all the flight logs associated with a particular flight permit and pass them on to this API to get in return a signed bundle.
    
    2. Flight Module Provider is responsible to provide communication interface to upload this bundle directly to the DSP or through external applications, such as Ground Control Station.

# Test Structure for Certification

The certification of registered flight modules would involve test cases covering secure provisioning of keys, implementation of Flight Module Management Server and Client, functional tests, security tests, and other compliance related tests.

It is required by Flight Module Providers to minimise the attack surface at the system level using methods such as but not limited to protective meshing, encrypted communication, etc. In addition, it is highly recommended that tamper responsiveness be implemented for the system.

Here are a list of example test cases:

| **Sr. No.** | **Type of Test**                                                                                                      |
| ----------- | --------------------------------------------------------------------------------------------------------------------- |
| 1           | Fake and authentic signed flight permit test                                                                          |
| 2           | Individual flight log storage test (including digital signature verification)                                         |
| 3           | Geofence breach flight log test                                                                                       |
| 4           | Time limit breach flight log test                                                                                     |
| 5           | Bundled flight log test (including digital signature verification)                                                    |
| 6           | RTH test in case of violation of permissions in the context of geofence 
|             | bounding box breach and max time-limit breach |
| 7           | Accidental storage data retrieval test with the specialized equipment                                                 |
| 8           | Overall no permission-no takeoff policy test                                                                          |
| 9           | Secure Boot and Secure Upgrade                                                                                        |
| 10          | Secure Provision of Keys                                                                                              |
| 11          | System Level Tamper Responsiveness                                                                                    |
| 12          | Any other test as defined by the Certification Agencies                                                               |

There will be certification agencies that will be empanelled to certify the RPAS, Registered Flight Module, etc. These agencies shall publish the detailed list of test requirements beforehand that would be necessary for certification.

> If you would like to test out your RFM Implementation, you may try out the open source test tool: [http://139.59.71.151](http://139.59.71.151/)
> In case you find any bugs or have any improvements, you may make the same here:[https://github.com/iSPIRT/NPNT-Provisional-testing-tool](https://github.com/iSPIRT/NPNT-Provisional-testing-tool)

# References

1. Requirements for Operation of Civil Remotely Piloted Aircraft System (RPAS): [CAR D3X-X1](http://dgca.nic.in/cars/D3X-X1.pdf)
1. [Information Technology Act](http://www.meity.gov.in/content/information-technology-act)
2. [Licensed CA](http://www.cca.gov.in/cca/?q=licensed_ca.html)

# Appendix

## General Safety Guidelines

1. **Firmware Tamper Avoidance:** *There is possibility to change firmware by the user so as to change the behaviour of the drone which might not follow laid guidelines under which the drone was originally cleared.*
    
    1. ReadOut Protection on MicroProcessor/MicroController for onboard firmware to avoid Copying of onboard keys and other sensitive information.
    
    2. Ensure keys are erased from memory during firmware update operation.
    
    3. Have authentication procedure to change Flight Parameters or have some parameters hidden or immutable unless Flight Module Provider supplies it post verification.

2. **Hardware Tamper Avoidance:** *There can be a possibility of changes to the onboard hardware like replacing Flight Controller or GLPS module, which might again lead to deviation from guidelines.*
    
    1. Secure Unique Identification of crucial hardwares like Radio Modules, GLPS and Flight Controller might be able to avoid this.

3. **Spoof Avoidance:** *Ensure that the Flight Controller can’t be run as hardware in the software loop by connecting over provided external interfaces, a feature available by default in many flight control softwares.*

4. **Link Hijack Avoidance**

5. **Drone System Failure Actions:** In cases of hardware or software failure, the drone system must have excessive audio visual notifications to raise alarm. Failures to Test for:
    
    1. GLPS Failure.
    
    2. Sensor Failure.
    
    3. Inability to hold altitude due to one or more onboard hardware failures.
    
    4. Battery Failure, if there is a power cut-off for any reason, the notification system be given isolated power for raising alarm.

> In addition to raising the audio visual alarms the drone system must initiate manual-mode recovery actions as decided by the manufacturer. In severe fault cases, the drone system must automatically trigger recovery actions as decided by the manufacturer.

## Registry of Certified Registered Flight Modules

The list of certified RFMs will be made available via a registry for third party applications to consume. These applications are expected to check with this registry during RFM service installation (if applications are managing these) and usage. There shall also be a registry for pre-certified RFM services.

## Registry of Digital Sky Service Providers

DGCA shall make available a machine readable list of all certified DSPs

## Evolving standardisation

Some of the topics under active discussion for revisions to this document are as follows. To keep up to date with the developments on these topics please refer to the [DSP Working Group](https://groups.google.com/forum/#!forum/drone-dsp) tracks for [proposals](https://github.com/iSPIRT/UFAMS/tree/master/proposals) and [standards](https://github.com/iSPIRT/UFAMS/tree/master/standards).

- RPAS Security
  - Implementation of Trusted Execution Environment
  - Implementation of pre-flight checks
  - Contingency scenarios in controlled airspace.
  - RPAS certificate management
  - Efficient and unambiguous encoding for data given to and generated from drones

- DigitalSky Service Provider
  - Services, scope and architecture guidelines  
    The proposed high level functionality under discussion include, among others: deconfliction before and during flights, support for flight planning by providing notifications of potentially conflicting flights, weather & terrain data. A few relatively open subtopics include management of drone ports, swarms and corridors and risk assessment. The ultimate goal for these functional services is to enable safe and informed UAS operation.
  - API specifications for data exchange between
    - UFII-DSP
    - DSP-DSP
  - Responsibility shift of management server to RFM and DSP and interoperability between DSP and hardware

- Remote ID & Telemetry
  - Broadcast and Network Hardware options & data exchange formats

- Documentation
  - Improving the Standards document for nomenclature.