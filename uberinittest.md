**MODIFY PRIOR EXECUTION**
uber post deposits api entry
https://developer.uber.com/docs/payments/references/testing/init-deposit-test

Resource
POST /v1/payments/deposits/:id/init

Auth
https://developer.uber.com/docs/riders/references/api/v2/token-post#example-request-access-token-client-credentials

funding_method	string	The payment method to be used to fund this deposit
country_iso2	string	The country in which this deposit is being created ISO3166
destination	<Object>	Should be left empty ({}) for this request
amount	<Object>	Value, Currency(ISO4217). The value is in E5 format. E.g., 10 BRL is represented as: {"value": 1000000, "currency": "BRL"}
locale	string	Locale to be used for UI experience

EXAMPLE REQUEST

curl -X POST \
  "https://sandbox-api.uber.com/v1/payments/deposits/$id/init"
  -H "Authorization: Bearer $token" \
  -H 'Content-Type: application/json' \
  -d '{
    "funding_method": "BOLETO",
    "country_iso2": "BR",
    "destination": {},
    "amount": {
      "value": 100000,
      "currency": "BRL"
    },
    "locale": "pt-BR"
  }'

********************************************************

RESPONSE

{
    "deposit_url": "https://api.partner.com/checkout?id=merchant_reference"
}