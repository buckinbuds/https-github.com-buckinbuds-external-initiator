**MODIFY PRIOR EXECUTION**
Deposits/Cancel api entry.
https://developer.uber.com/docs/payments/references/api/v1.2/deposits-cancel-deposit_id-post

Body param: cancel_reason / user_cancelled / merchant_expired / merchant_rejected

Request headers

X-Idempotency-Key

Replace "$token" in the example below with the access token:

curl -X POST \
  "https://sandbox-api.uber.com/v1/payments/deposits/3dad6604-c805-4153-9286-b58dca9b6ca7/cancel" \
  -H "Authorization: Bearer $token" \
  -H 'X-Idempotency-Key: 3dad6604-c805-4153-9286-b58dca9b6ca7-cancel' \
  -H 'Content-Type: application/json' \
  -d '{
    "cancel_reason": "USER_CANCELLED"
}'

**********************************************************

RESPONSE

{
  "deposit": {
    "id": "3dad6604-c805-4153-9286-b58dca9b6ca7",
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
      "value": "CANCELLED",
      "detail": "USER_CANCELLED"
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