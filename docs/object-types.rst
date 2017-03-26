.. _object-types:

Object Types
============

.. _Address:

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

.. _Company:

Company
-------

**JSON Object example**

.. code-block:: json

	{
		"name": "My Organization",
		"vat_id": "FR27654654654",
		"siren_id": "654654654",
		"siret_id": "65465465400045",
		"address": {},
		"phone": "+33401010101",
		"contacts": []
	}

**Attributes**

- **`name`** Required. *The name of the company*. type: string. format: alphanumeric.
- **`vat_id`** Optional. *VAT Identification Number of the company*. type: string. format: alphanumeric.
- **`siren_id`** Required. *SIREN Identification Number of the company (for french companies only)*. type: string. format: numeric.
- **`siret_id`** Optional. *SIRET Identification Number of the company branch (for french companies only)*. type: string. format: numeric.
- **`address`** Required. *Address of the company*. type: object Address_.
- **`phone`** Optional. *Contact phone number of the company*. type: string. format: valid phone number.
- **`contacts`** Optional. *Contacts of the company*. type: Array(object Contact_).

.. _Contact:

Contact
-------

**JSON Object example**


.. code-block:: json

	{
		"firstname": "John",
		"lastname": "Doe",
		"email": "john.doe@company.com",
		"phone": "+33601010101",
		"address": { }
	}

**Attributes**

- **`firstname`** : *Firstname of the contact*. type: string. format: alpha.
- **`lastname`** : *Lastname of the contact*. type: string. format: alpha.
- **`email`** : *Email of the contact*. type: string. format: valid email.
- **`phone`** : *Phone number of the contact*. type: string. format: valid phone number as defined by E.164, the international public telecommunication numbering plan.
- **`address`** Optional. *Address of the contact*. type: object Address_.

.. _Invoice:

Invoice
-------

**JSON Object example**


.. code-block:: json

	{
		"app_invoice_id": "1234",
		"sender": {
			"type": "professional",
			"company": { },
			"contact": { },
		},
		"receiver": {
			"app_receiver_id": "MYCUSTOMER-45",
			"type": "professional",
			"company": { },
			"contact": { },
		},
		"delivery_address": { },
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
		"lines": [],
		"journal_entries": []
	}

**Attributes**

- **`app_invoice_id`** Required. *Invoice identifier of the third party application.* type: string. format: alphanumeric.
- **`sender`** Required. *The sender of the invoice*.
- **`sender[type]`** Required. type: string. values: `'professional'`.
- **`sender[company]`** Required. *The company of the sender*. type: object Company_.
- **`sender[contact]`** Optional. type: object Contact_.
- **`receiver`** Required. *The receiver of the invoice*.
- **`receiver[app_receiver_id]`** Required. *Receiver identifier of the third party application.* type: string. format: alphanumeric.
- **`receiver[type]`** Required. type: string. values: `'professional'` | `'institutional'` | `'individual'`.
- **`receiver[company]`** Required if type is `professional`. *The company of the receiver*. type: object Company_.
- **`receiver[contact]`** Required if type is `individual`. type: object Contact_.
- **`delivery_address`** Optional. *Invoice's Delivery Address.* type: object Address_.
- **`reference`** Required. *Invoice reference number.* type: string. format: alphanumeric.
- **`issue_date`** Required. type: string. format: date.
- **`invoice_type_code`** Required. *Type of the invoice*. type: char. value:s `'S'` (standard) | `'C'` (credit note).
- **`currency_code`** Required. *Currency used in invoice format*. type: string. format: 3 digits as defined by [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html).
- **`total`** Required. *Total amount of the invoice before taxes*. type: decimal. 
- **`taxes`** Required. *Taxes amount of the invoice*. type: decimal.
- **`total_due`** Required. *Total amount of the invoice including taxes*. type: decimal.
- **`journal_entries`** Optional. *Invoice's journal entries*. type: Array(object JournalEntry_).
- **`terms`**: {due_date}
- **`lines`** Required. *Invoice lines*. type: Array(object InvoiceLine_).
- **`journal_entries`** Optional. *Invoice's journal entries*. type: Array(object JournalEntry_).

.. _InvoiceLine:

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
- **`items`** Required. *Line items*. type: Array(object InvoiceLineItem_)

.. _InvoiceLineItem:

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
- **`journal_entries`** Optional. *Item's journal entries*. type: Array(object JournalEntry_).

.. _JournalEntry:

JournalEntry
------------


**JSON Object example**

.. code-block:: json

	{
		"app_journal_id": "2",
		"journal_code": "SA",
		"journal_description": "Sales",
		"account_number": "445710",
		"description": "Collected VAT",
		"debit": 0,
		"credit": 310.54
	}


**Attributes**

- **`app_journal_id`** Optional. *Journal ID of the accounting journal*. type: string. format: alphanumeric.
- **`journal_code`** Optional. *Journal code of the accounting journal*. type: string. format: alphanumeric.
- **`journal_description`** Optional. *Journal description of the accounting journal*. type: string. format: alphanumeric.
- **`account_number`** Required. *Account number for the accounting entry*. type: string. format: alphanumeric.
- **`account_description`** Optional. *Account description*. type: string. format: alphanumeric
- **`debit`** Required. *Debit amount*. type: decimal
- **`credit`** Required. *Credit amount*. type: decimal