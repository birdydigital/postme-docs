# Send invoices

*Documentation in progress*


__Resource__

|URL|`/api/invoices`|
|:---|---|
|Method|POST|

__ Request payload example __


```
{
	"app_invoice_id": "1234",
	"sender": {

	},
	"receiver": {

	},
	"receiver_type": "professional",
	"reference": "INV201701010004",
	"issue_date": "2017-01-01",
	"invoice_type_code": "S",
	"currency_code": "EUR",
	"total": 100,
	"taxes": 5.5,
	"total_due": 105.5,
	"terms": {
		"due_date": "2017-02-01"
	},
	"lines": [
		{
			"total": 100,
			"taxes": 5.5,
			"total_due": 105.5,
			"items": [
				{
					"lot_id": "ABCDE12345",
					"description": "Beef steak",
					"quantity": 12.5,
					"unit": "kg",
					"unit_price": 4,
					"total": 50,
					"taxes": 2.75,
					"total_due": 52.75
				},
				{
					"lot_id": "FGHIJ67890",
					"description": "Pork steak",
					"quantity": 10,
					"unit": "kg",
					"unit_price": 5,
					"total": 50,
					"taxes": 2.75,
					"total_due": 52.75
				}

			]
		}
	]
}
```

---

__Parameters__

*All parameters prefixed with `app_` refer to the third party application data.*

__Invoice__

- __`app_invoice_id`__ 

Required.
*Invoice identifier of the third party application.*
type: string
format: alphanumeric

- __`sender`__

Required
*Sender of the invoice*
type: `Company`

- __`receiver`__

Required
type: `Contact`|`Company`

- __`receiver_type`__

Required
type: string
format: `'professional'` | `'institutional'` | `'individual'`

- __`reference`__

Required
type: string
format: alphanumeric
Invoice reference number.

- __`issue_date`__

Required
type: string
format: date

- __`invoice_type_code`__

Required
*Type of the invoice*
type: char
format: `'S'` (standard) | `'C'` (credit note)

- __`currency_code`__

Required
*Currency used in invoice format*
type: string
format: [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) 

- __`total`__

Required
*Total amount of the invoice before taxes*
type: decimal

- __`taxes`__

Required
*Taxes amount of the invoice*
type: decimal

- __`total_due`__

Required
*Total amount of the invoice including taxes*
type: decimal

- `terms`: {due_date}

- __`lines`__

Required
*Invoice lines*
type: `InvoiceLine`


__Invoice Line__

- __`total`__

Required
*Total amount of the invoice line before taxes*
type: decimal

- __`taxes`__

Required
*Taxes amount of the invoice line*
type: decimal

- __`total_due`__

Required
*Total amount of the invoice line including taxes*
type: decimal

- `items`

__Invoice Line Item__

- __`lot_id`__

Optional
*Item's lot identification number*
type: string
format: alphanumeric

- __`description`__

Required
type: string
format: alphanumeric

- __`quantity`__

Optional
type: decimal

- __`unit`__

Optional
type: string
format: alphanumeric

- __`unit_price`__

Optional
type: decimal

- __`total`__

Required
*Total amount of the invoice line item before taxes*
type: decimal

- __`taxes`__

Required
*Taxes amount of the invoice line item*
type: decimal

- __`total_due`__

Required
*Total amount of the invoice line item including taxes*
type: decimal

- `accounting_entries` *optional*

__Company__

- `name`
- `vat_id`
- `siret_id`
- `apet_id`
- `address`
- `contacts`

__Contact__

- `name`
- `telephone`
- `email`

__Accounting Entry__

- `account_number`
- `debit`
- `credit`
