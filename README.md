# Unified Flight and Airspace Management Specification (UFAMS)

## API Endpoints

## Schemas

See [schemas](schemas), [examples](schemas/examples/README.md) and descriptions below.

### Device Registration 

- URL: https://{baseUrl}/api/v1/droneDevice/register/<manufacturerBusinessIdentifier>
- Request Method: POST
- Signing Algorithm: RSASSA-PKCS1-v1_5 SHA-256

The registration request to the server should be constructed as per JWS specification (IETF RFC7515). The registration data payload specified above should be encoded in base64 encoding and signed using Flight Module Provider Private Key securely through PKI Token/HSM.

Schemas: [schemas](schemas/endpoints/v1/device-registration)

### Device Deregistration 
- URL: https://{baseUrl}/api/v1/droneDevice/deregister/<manufacturerBusinessIdentifier>
- Request Method: POST
- Signing Algorithm: RSASSA-PKCS1-v1_5 SHA-256

The registration request to the server should be constructed as per JWS specification (IETF RFC7515). The registration data payload specified above should be encoded in base64 encoding and signed using Flight Module Provider Private Key securely through PKI Token/HSM.

Schemas: [schemas](schemas/endpoints/v1/device-deregistration)

## Flight Log
The flight log should be constructed as per JWS specification (IETF RFC7515). The TBS flight log payload should be encoded in base64 encoding and signed using Flight Module Private Key.

Refer to [schemas](schemas/flight-log/v1) for flight log schema.

## Proposals Track
Proposals that are currently under consideration or review will be available in the [proposals](proposals) directory.

## Standards Track
Proposals that have been accepted will be available in the [standards](standards/) directory.

### Standards Document
Earlier this was refered to as RPAS Guidance Manual, or Technology standards document. To build a PDF version of the document, refer to [this readme](./document/README.md).