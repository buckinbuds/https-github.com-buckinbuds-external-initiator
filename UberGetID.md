**MODIFY PRIOR EXECUTION**
GET_ID api entry.
https://developer.uber.com/docs/payments/references/api/v1.2/deposits-deposit_id-get

EXAMPLE REQUEST

Replace "$token" in the example below with the access token:

curl "https://sandbox-api.uber.com/v1/payments/deposits/ad18f686-84dc-4255-841b-5f2153c70887" -H "Authorization: Bearer $token"

**************************************************************************************

RESPONSE

{
  "deposit": {
    "id": "ad18f686-84dc-4255-841b-5f2153c70887",
    "destination": {
      "id": "cHBfNjFhN2QyODktZmI3Mi00YzgxLThlYjAtODRlZDIyMjFmNDNi",
      "owner_id": "105b9291-6ff1-4938-899e-4bfafa69a6c7",
      "type": "Account",
      "uri": "//payments/customers/105b9291-6ff1-4938-899e-4bfafa69a6c7/accounts/cHBfNjFhN2QyODktZmI3Mi00YzgxLThlYjAtODRlZDIyMjFmNDNi"
    },
    "source": {
      "id": "Z3NfYTE0OGQ5MzMtOGVkMS00MzA0LThiNzAtNTE0MjMyMzg2MjQw",
      "owner_id": "a7b46663-3b97-40be-9b3e-ab805a56b269",
      "type": "Account",
      "uri": "//payments/customers/a7b46663-3b97-40be-9b3e-ab805a56b269/accounts/Z3NfYTE0OGQ5MzMtOGVkMS00MzA0LThiNzAtNTE0MjMyMzg2MjQw"
    },
    "state": {
      "value": "CONFIRMED"
    },
    "amount": {
      "value": 100000,
      "currency": "BRL"
    },
    "description": "I'm a deposit in sandbox.",
    "merchant_reference": "599f4164-4417-4361-9d11-1d9d8b4b9096",
    "country_iso2": "BR",
    "created_at": "2019-04-10T12:00:00Z",
    "updated_at": "2019-04-11T12:00:00Z",
    "session_id": "8b31b7f4-3542-4391-817c-d496ce84a7ae",
    "funding_method": "BOLETO",
    "type": "Deposit",
    "uri": "//payments/deposits/86108b55-69a5-48a1-9415-cb8426d6e2ef"
  }
}