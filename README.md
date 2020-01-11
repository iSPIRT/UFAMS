# Unified Flight and Airspace Management Specification (UFAMS)

## API Endpoints

### Device Registration 

- URL: https://{baseUrl}/api/v1/droneDevice/register/<manufacturerBusinessIdentifier>
- Request Method: POST
- Signing Algorithm: RSASSA-PKCS1-v1_5 SHA-256

The registration request to the server should be constructed as per JWS specification (IETF RFC7515). The registration data payload specified above should be encoded in base64 encoding and signed using Flight Module Provider Private Key securely through PKI Token/HSM.

Schemas: schemas/endpoints/v1/device-registration

### Device Deregistration 
- URL: https://{baseUrl}/api/v1/droneDevice/deregister/<manufacturerBusinessIdentifier>
- Request Method: POST
- Signing Algorithm: RSASSA-PKCS1-v1_5 SHA-256

The registration request to the server should be constructed as per JWS specification (IETF RFC7515). The registration data payload specified above should be encoded in base64 encoding and signed using Flight Module Provider Private Key securely through PKI Token/HSM.

Schemas: schemas/endpoints/v1/device-deregistration

