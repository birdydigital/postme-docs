.. _object-types:

Object Types
============


Address
----------

**JSON Object example**


.. code-block:: json

	{
		"address_1": "",
		"address_2": "",
		"postal_code": "69003",
		"city": "Lyon",
		"country_code": "FRA"
	}

**Attributes**

- **`address_1`** : Required. *Address 1*. type: string. format: alphanumeric, max length: 255 char.
- **`address_2`** : Optional. *Address 2*. type: string. format: alphanumeric, max length: 255 char.
- **`postal_code`** : Required. *Postal Code*. type: string. format: alphanumeric, max length: 16 char.
- **`city`** : Required. *Postal Code*. type: string. format: alphanumeric, max length: 64 char.
- **`country_code`** : Required. *Country code of the address*. type: string. format: 2 digits As defined by the ISO 3166-1 alpha-2.


Company
-------

**JSON Object example**

.. code-block:: json

	{
		"name": "My Organization",
		"vat_id": "FR27654654654",
		"siren_id": "654654654",
		"address": {},
		"phone": "+33401010101",
		"contacts": []
	}

**Attributes**

- **`name`** Required. *The name of the company*. type: string. format: alphanumeric.
- **`vat_id`** Required. *VAT Identification Number of the company*. type: string. format: alphanumeric.
- **`siren_id`** Required. *SIREN Identification Number of the company (for french companies only)*. type: string. format: numeric.
- **`address`** Required. *Address of the company*. type: object Address (please refer to the Object Types > Address section).
- **`phone`** Optional. *Contact phone number of the company*. type: string. format: valid phone number.
- **`contacts`** Optional. *Contacts of the company*. type: Array(object Contact).

Contact
-------

**JSON Object example**


.. code-block:: json

	{
		"firstname": "John",
		"lastname": "Doe",
		"email": "john.doe@company.com",
		"phone": "+33601010101",
	}

**Attributes**

- **`firstname`** : *Firstname of the contact*. type: string. format: alpha.
- **`lastname`** : *Lastname of the contact*. type: string. format: alpha.
- **`email`** : *Email of the contact*. type: string. format: valid email.
- **`phone`** : *Phone number of the contact*. type: string. format: valid phone number as defined by E.164, the international public telecommunication numbering plan.

.. _object-invoice:

Invoice
-------

**JSON Object example**


.. code-block:: json

	{
		"app_invoice_id": "1234",
		"sender_type": "professional",
		"sender": {},
		"receiver_type": "professional",
		"receiver": {},
		"reference": "INV201701010004",
		"issue_date": "2017-01-01",
		"invoice_type_code": "S",
		"currency_code": "EUR",
		"total": 100,
		"taxes": 5.5,
		"total_due": 105.5,
		"journal_entries": [],
		"terms": {
			"due_date": "2017-02-01"
		},
		"lines": []

	}

**Attributes**

- **`app_invoice_id`** Required. *Invoice identifier of the third party application.* type: string. format: alphanumeric.
- **`sender_type`** Required. type: string. values: `'professional'`.
- **`sender`** Required. *Sender of the invoice*. type: object Company.
- **`receiver_type`** Required. type: string. values: `'professional'` | `'institutional'` | `'individual'`.
- **`receiver`** Required. type: object Contact | object Company.
- **`reference`** Required. *Invoice reference number.* type: string. format: alphanumeric.
- **`issue_date`** Required. type: string. format: date.
- **`invoice_type_code`** Required. *Type of the invoice*. type: char. value:s `'S'` (standard) | `'C'` (credit note).
- **`currency_code`** Required. *Currency used in invoice format*. type: string. format: 3 digits as defined by [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html).
- **`total`** Required. *Total amount of the invoice before taxes*. type: decimal. 
- **`taxes`** Required. *Taxes amount of the invoice*. type: decimal.
- **`total_due`** Required. *Total amount of the invoice including taxes*. type: decimal.
- **`journal_entries`** Optional. *Invoice's journal entries*. type: Array(object JournalEntry).
- **`terms`**: {due_date}
- **`lines`** Required. *Invoice lines*. type: Array(object InvoiceLine).


InvoiceLine
-----------

**JSON Object example**


.. code-block:: json

	{
		"total": 100,
		"taxes": 5.5,
		"total_due": 105.5,
		"items": []
	}

**Attributes**


- **`total`** Required. *Total amount of the invoice line before taxes*. type: decimal.
- **`taxes`** Required. *Taxes amount of the invoice line*. type: decimal.
- **`total_due`** Required. *Total amount of the invoice line including taxes*. type: decimal. 
- **`items`** Required. *Line items*. type: Array(object InvoiceLineItem)


InvoiceLineItem
---------------

**JSON Object example**

.. code-block:: json

	{
		"lot_id": "ABCDE12345",
		"description": "Beef steak",
		"quantity": 12.5,
		"unit": "kg",
		"unit_price": 4,
		"total": 50,
		"taxes": 2.75,
		"total_due": 52.75,
		"journal_entries": []
	}

**Attributes**

- **`lot_id`** Optional. *Item's lot identification number*. type: string. format: alphanumeric
- **`description`** Required. type: string. format: alphanumeric. 
- **`quantity`** Optional. type: decimal. 
- **`unit`** Optional. type: string. format: alphanumeric
- **`unit_price`** Optional. type: decimal. 
- **`total`** Required. *Total amount of the invoice line item before taxes*. type: decimal.
- **`taxes`** Required. *Taxes amount of the invoice line item*. type: decimal. 
- **`total_due`** Required. *Total amount of the invoice line item including taxes*. type: decimal. 
- **`journal_entries`** Optional. *Item's journal entries*. type: Array(object JournalEntry).


JournalEntry
------------


**JSON Object example**

.. code-block:: json

	{
		"account_number": "411",
		"description": "Customer taxes",
		"credit": 0,
		"debit": 310.54
	}


**Attributes**

- **`account_number`** Required. *Account number for the accounting entry*. type: string. format: alphanumeric.
- **`description`** Optional. *Account description*. type: string. format: alphanumeric
- **`debit`** Required. *Debit amount*. type: decimal
- **`credit`** Required. *Credit amount*. type: decimal