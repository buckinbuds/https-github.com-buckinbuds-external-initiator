**MODIFY PRIOR EXECUTION**
Uber_SIGVALIDATOIN API entry
https://developer.uber.com/docs/payments/references/testing/signature-validation

**READ ME FIRST**
Note #1: Please be aware that for openssl validation command to work properly, both DECODED_HEADERS_FILE and SIGNATURE_FILE should not have a line ending character at the end of the file.

Note #2: host header included in the verification headers as stated in the example above, should only include :{PORT} in case of non-standard ports for the given scheme. To give an example, since port 443 is the default port for the https scheme, it won’t be included in the resulting host header text in the above example with URL https://uber.partner.com/v1/payments/init-deposit. If the URL would be https://uber.partner.com:9443/v1/payments/init-deposit instead, then the resulting host header should have been uber.partner.com:9443.

Note #3: The order of the header items are important for the signature validation, and it should be in the order of (request-target), host, date, digest.

Troubleshoot:
https://www.openssl.org/source/

openssl dgst -sha256 -verify {PUBLIC_KEY_FILE} -signature {SIGNATURE_FILE} {DECODED_HEADERS_FILE}

**********************************

sandbox:

-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAnYzMrDq+EnccKtcs5gQM
uP5aDe9WzdBGyUiervrFCEXmVW+T2nsSKJJR02H84LBKPjz2ioI3L289q1Qx1gj7
gvV9VZCaKejIsdKWnM5QW/1VvARWL2diScZzp5OxKX78X8aevvts79B9cVZUiEOU
E4+TTe9qLOQvbc9SssTbdqiA+1xqU+wW7IfHm5cC5kLb+Kv3pqJ63lMTx2L1iNuO
xinwun8lpdRl2+c7LswqqpUfI7Hfk0QF/XJO01BXsDxCzxkuHoWa4SNL+gNx3M69
vc5ymlZHJNZRPLMIe4+VVRaDe0dCOUcHz3cmXCjkLKfdd3JFAG+8FU/CvE1qzyP4
pwIDAQAB
-----END PUBLIC KEY-----

***********************************

example request:

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
  -H 'X-Correlation-ID: c900d4dd-7070-4e0b-9323-8f24cfde0490' \
  -H 'Content-Type: application/json' \
  -d '{
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
    "return_url": "uber://payments/deposit?correlation_id=c900d4dd-7070-4e0b-9323-8f24cfde0490"
}'

*********************

echo Y8A9LQ52bWClisGSzE1+FirYDPloQLtp6UxuBHojjQj/aSfYkUHz85OSjhfNj8p0LiOHo94xX17cO3X61gsbliMbog+ULuMmxmOhjmm8S3Bi85260+4aoBNbIEC9pSVIEFkwToPBq8Oe38TdG1LlaUA7vuWw6JO6ineoMRbuFao= | base64 -D

*********************

(request-target): post /v1/payments/init-deposit
host: uber.partner.com
date: Sat, 08 Jun 2019 20:51:35 GMT
digest: SHA-256=FkJ3miKx7I099a8n7q3Kmn7P8/dFS1Ebx5POQd185PM=