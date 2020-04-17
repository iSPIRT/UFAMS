### Send Remote Id Message

- URL: https://{baseUrl}/api/v1/remote_id_message
- Request Method: POST
- Signing Algorithm: RSASSA-PKCS1-v1_5 SHA-256

The registration request to the server should be constructed as per JWS specification (IETF RFC7515). The registration data payload specified above should be encoded in base64 encoding and signed using Flight Module Provider Private Key securely through PKI Token/HSM.

Schema: [Send Remote Id Message](proposals/npnt-network-remote-id/endpoints/send-message)
