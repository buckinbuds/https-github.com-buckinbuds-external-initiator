**MODIFY PRIOR EXECUTION**
for API entry.
https://developer.uber.com/docs/payments/references/api/v1.2/init-deposit
Partner Inital Deposit
RSA-SHA256 Sig with uber payments pubkey. See signature:
https://tools.ietf.org/html/draft-cavage-http-signatures-11#section-4.1.1

Sandbox:

-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAnYzMrDq+EnccKtcs5gQM
uP5aDe9WzdBGyUiervrFCEXmVW+T2nsSKJJR02H84LBKPjz2ioI3L289q1Qx1gj7
gvV9VZCaKejIsdKWnM5QW/1VvARWL2diScZzp5OxKX78X8aevvts79B9cVZUiEOU
E4+TTe9qLOQvbc9SssTbdqiA+1xqU+wW7IfHm5cC5kLb+Kv3pqJ63lMTx2L1iNuO
xinwun8lpdRl2+c7LswqqpUfI7Hfk0QF/XJO01BXsDxCzxkuHoWa4SNL+gNx3M69
vc5ymlZHJNZRPLMIe4+VVRaDe0dCOUcHz3cmXCjkLKfdd3JFAG+8FU/CvE1qzyP4
pwIDAQAB
-----END PUBLIC KEY-----

Example Request below:
https://uber.partner.com/v1/payments/init-deposit

curl -X POST \
  https://uber.partner.com/v1/payments/init-deposit \
  -H 'Accept-Language: pt-BR' \
  -H 'Date: Sat, 08 Jun 2019 20:51:35 GMT' \
  -H 'Digest: SHA-256=FkJ3miKx7I099a8n7q3Kmn7P8/dFS1Ebx5POQd185PM=' \
  -H 'Signature: keyId="rsa-key", algorithm="rsa-sha256",
     headers="(request-target) host date digest",
     signature="Y8A9LQ52bWClisGSzE1+FirYDPloQLtp6UxuBHojjQj/aSfYkUHz
       85OSjhfNj8p0LiOHo94xX17cO3X61gsbliMbog+ULuMmxmOhjmm8S3Bi85260
       +4aoBNbIEC9pSVIEFkwToPBq8Oe38TdG1LlaUA7vuWw6JO6ineoMRbuFao="'
  -H 'Content-Type: application/json' \
  -d '{
    "id": "c900d4dd-7070-4e0b-9323-8f24cfde0490",
    "destination": {
      "owner_id": "105b9291-6ff1-4938-899e-4bfafa69a6c7",
      "id": "cHBfNjFhN2QyODktZmI3Mi00YzgxLThlYjAtODRlZDIyMjFmNDNi"
    },
    "source": {
      "owner_id": "a66b36d5-887c-4e7c-9edb-9fcbef108e83",
      "id": "Z3NfYTE0OGQ5MzMtOGVkMS00MzA0LThiNzAtNTE0MjMyMzg2MjQw"
    },
    "amount": {
      "value": 100000,
      "currency": "BRL"
    },
    "description": "I\'m a deposit in sandbox.",
    "country_iso2": "BR",
    "funding_method": "BOLETO",
    "initiated_at": "2019-06-08T20:51:35Z",
    "session_id": "8b31b7f4-3542-4391-817c-d496ce84a7ae",
    "return_url": "uber://payments/deposit?correlation_id=c900d4dd-7070-4e0b-9323-8f24cfde0490",
    "destination_owner": {
        "type": "Customer",
        "id": "a66b36d5-887c-4e7c-9edb-9fcbef108e83",
        "uri": "//payments/customers/a66b36d5-887c-4e7c-9edb-9fcbef108e83",
        "details": {
            "mobile": "+123456788",
            "firstname": "John",
            "lastname": "Doe"
        }
    }
}'

EXMAPLE RESPONSE:
HTTP/1.1 201 Created
Location: https://api.partner.com/checkout?id=merchant_reference