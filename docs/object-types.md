## Address

__JSON Object example__


```
{
	"address_1": "",
	"address_2": "",
	"postal_code": "69003",
	"city": "Lyon",
	"country_code": "FRA"
}
```

__Attributes__

- __`address_1`__ : Required. *Address 1*. type: string. format: alphanumeric, max length: 255 char.
- __`address_2`__ : Optional. *Address 2*. type: string. format: alphanumeric, max length: 255 char.
- __`postal_code`__ : Required. *Postal Code*. type: string. format: alphanumeric, max length: 16 char.
- __`city`__ : Required. *Postal Code*. type: string. format: alphanumeric, max length: 64 char.
- __`country_code`__ : Required. *Country code of the address*. type: string. format: 2 digits As defined by the ISO 3166-1 alpha-2.

___

## Company

__JSON Object example__


```
{
	"name": "My Organization",
	"vat_id": "FR27654654654",
	"siren_id": "654654654",
	"address": {
		...
	},
	"phone": "+33401010101",
	"contacts": [
		...
	]
}
```

__Attributes__

- __`name`__ Required. *The name of the company*. type: string. format: alphanumeric.
- __`vat_id`__ Required. *VAT Identification Number of the company*. type: string. format: alphanumeric.
- __`siren_id`__ Required. *SIREN Identification Number of the company (for french companies only)*. type: string. format: numeric.
- __`address`__ Required. *Address of the company*. type: object Address (please refer to the Object Types > Address section).
- __`phone`__ Optional. *Contact phone number of the company*. type: string. format: valid phone number.
- __`contacts`__ Optional. *Contacts of the company*. type: Array(object Contact).

___


## Contact

__JSON Object example__


```
{
	"firstname": "John",
	"lastname": "Doe",
	"email": "john.doe@company.com",
	"phone": "+33601010101",
}
```

__Attributes__

- __`firstname`__ : *Firstname of the contact*. type: string. format: alpha.
- __`lastname`__ : *Lastname of the contact*. type: string. format: alpha.
- __`email`__ : *Email of the contact*. type: string. format: valid email.
- __`phone`__ : *Phone number of the contact*. type: string. format: valid phone number as defined by E.164, the international public telecommunication numbering plan.

___

## Invoice

__JSON Object example__


```
{
	"app_invoice_id": "1234",
	"sender_type": "professional",
	"sender": {
		...
	},
	"receiver_type": "professional",
	"receiver": {
		...
	},
	"reference": "INV201701010004",
	"issue_date": "2017-01-01",
	"invoice_type_code": "S",
	"currency_code": "EUR",
	"total": 100,
	"taxes": 5.5,
	"total_due": 105.5,
	"journal_entries": [
		...
	],
	"terms": {
		"due_date": "2017-02-01"
	},
	"lines": [
		...
	]

}
```

__Attributes__

- __`app_invoice_id`__ Required. *Invoice identifier of the third party application.* type: string. format: alphanumeric.
- __`sender_type`__ Required. type: string. values: `'professional'`.
- __`sender`__ Required. *Sender of the invoice*. type: object Company.
- __`receiver_type`__ Required. type: string. values: `'professional'` | `'institutional'` | `'individual'`.
- __`receiver`__ Required. type: object Contact | object Company.
- __`reference`__ Required. *Invoice reference number.* type: string. format: alphanumeric.
- __`issue_date`__ Required. type: string. format: date.
- __`invoice_type_code`__ Required. *Type of the invoice*. type: char. value:s `'S'` (standard) | `'C'` (credit note).
- __`currency_code`__ Required. *Currency used in invoice format*. type: string. format: 3 digits as defined by [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html).
- __`total`__ Required. *Total amount of the invoice before taxes*. type: decimal. 
- __`taxes`__ Required. *Taxes amount of the invoice*. type: decimal.
- __`total_due`__ Required. *Total amount of the invoice including taxes*. type: decimal.
- __`journal_entries`__ Optional. *Invoice's journal entries*. type: Array(object JournalEntry).
- __`terms`__: {due_date}
- __`lines`__ Required. *Invoice lines*. type: Array(object InvoiceLine).

## InvoiceLine

__JSON Object example__


```
{
	"total": 100,
	"taxes": 5.5,
	"total_due": 105.5,
	"items": [
		...
	]
}
```

__Attributes__


- __`total`__ Required. *Total amount of the invoice line before taxes*. type: decimal.
- __`taxes`__ Required. *Taxes amount of the invoice line*. type: decimal.
- __`total_due`__ Required. *Total amount of the invoice line including taxes*. type: decimal. 
- __`items`__ Required. *Line items*. type: Array(object InvoiceLineItem)


## InvoiceLineItem

__JSON Object example__

```
{
	"lot_id": "ABCDE12345",
	"description": "Beef steak",
	"quantity": 12.5,
	"unit": "kg",
	"unit_price": 4,
	"total": 50,
	"taxes": 2.75,
	"total_due": 52.75,
	"journal_entries": [
		...
	]
}
```

__Attributes__

- __`lot_id`__ Optional. *Item's lot identification number*. type: string. format: alphanumeric
- __`description`__ Required. type: string. format: alphanumeric. 
- __`quantity`__ Optional. type: decimal. 
- __`unit`__ Optional. type: string. format: alphanumeric
- __`unit_price`__ Optional. type: decimal. 
- __`total`__ Required. *Total amount of the invoice line item before taxes*. type: decimal.
- __`taxes`__ Required. *Taxes amount of the invoice line item*. type: decimal. 
- __`total_due`__ Required. *Total amount of the invoice line item including taxes*. type: decimal. 
- __`journal_entries`__ Optional. *Item's journal entries*. type: Array(object JournalEntry).

## JournalEntry

__JSON Object example__

```
{
	"account_number": "411",
	"description": "Customer taxes",
	"credit": 0,
	"debit": 310.54
}
```

__Accounting Entry__

- __`account_number`__ Required. *Account number for the accounting entry*. type: string. format: alphanumeric.
- __`description`__ Optional. *Account description*. type: string. format: alphanumeric
- __`debit`__ Required. *Debit amount*. type: decimal
- __`credit`__ Required. *Credit amount*. type: decimal