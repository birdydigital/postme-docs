.. data-models:

Data Models
===========

.. _Address:

Address
-------

**Structure**


.. code-block:: json

	{
		"address_1": "",
		"address_2": "",
		"postal_code": "69003",
		"city": "Lyon",
		"country_code": "FR"
	}

**Attributes**

- ``address_1`` : Required. *Address 1*. type: string. format: alphanumeric, max length: 255 char.
- ``address_2`` : Optional. *Address 2*. type: string. format: alphanumeric, max length: 255 char.
- ``postal_code`` : Required. *Postal Code*. type: string. format: alphanumeric, max length: 16 char.
- ``city`` : Required. *Postal Code*. type: string. format: alphanumeric, max length: 64 char.
- ``country_code`` : Required. *Country code of the address*. type: string. format: 2 digits As defined by the ISO 3166-1 alpha-2.

.. _Company:

Company
-------

**Structure**

.. code-block:: json

	{
		"name": "My Organization",
		"address": {},
		"identification": {
			"siren_id": "654654654",
			"vat_id":   "FR27654654654",
			"siret_id": "65465465400045",
		}
	}

**Attributes**

- ``name`` Required. *The name of the company*. type: string. format: alphanumeric.
- ``address`` Required. *Address of the company*. type: object Address_.
- ``identification`` Required. *Identification of the company*. type: object. *Required fields are based on company's address country_code*
	- ``siren_id`` 'FR': Required. *SIREN Identification Number of the company (for french companies only)*. type: string. format: numeric.
	- ``vat_id`` Optional. *VAT Identification Number of the company*. type: string. format: alphanumeric.
	- ``siret_id`` Optional. *SIRET Identification Number of the company branch (for french companies only)*. type: string. format: numeric.

.. _Contact:

Contact
-------

**Structure**


.. code-block:: json

	{
		"name": "John Doe (accounting service)",
		"email": "john.doe@company.com",
		"phone": "+33601010101",
		"address": { }
	}

**Attributes**

- ``name`` Required. *Name of the contact*. type: string. format: alpha.
- ``email`` Required. *Email of the contact*. type: string. format: valid email.
- ``phone`` Optional. *Phone number of the contact*. type: string. format: valid phone number as defined by E.164, the international public telecommunication numbering plan.
- ``address`` Optional. *Address of the contact*. type: object Address_.

.. _Invoice:

Invoice
-------

**Structure**


.. code-block:: json

	{
		"app_invoice_id": "1234",
		"seller_party": {
			"app_party_id": "123123",
			"type": "professional",
			"company": { },
			"contacts": [ ]
		},
		"buyer_party": {
			"app_party_id": "456456",
			"type": "professional",
			"company": { },
			"contacts": [ ],
			"person": { }
		},
		"delivery_address": { },
		"reference": "INV201701010004",
		"description": "My first invoice",
		"issue_date": "2017-01-01",
		"invoice_type_code": "S",
		"currency_code": "EUR",
		"taxes": [
			{
				"tax_rate": 5.5,
				"total": 200,
				"total_taxes": 11,
				"total_due": 211
			},
			{
				"tax_rate": 19.6,
				"total": 1000,
				"total_taxes": 196,
				"total_due": 1196
			}
		],
		"total": 1200,
		"total_taxes": 207,
		"total_due": 1407,
		"terms": {
			"due_date": "2017-02-01",
			"payment": "Before Jun 31st",
			"vat": "Not applicable"
		},
		"lines": [],
		"journal_entries": [],
		"notes": "Some free text..."
	}

**Attributes**

- ``app_invoice_id`` Required. *Invoice identifier of the third party application*. type: string. format: alphanumeric.
- ``seller_party`` Required. *The seller party of the invoice*.
- ``seller_party[app_party_id]`` Required. *Party identifier of the third party application.* type: string. format: alphanumeric.
- ``seller_party[type]`` Required. type: string. values: `'professional'`.
- ``seller_party[company]`` Required. *The company of the seller party*. type: object Company_.
- ``seller_party[contacts]`` Required. *Administrative contacts of the seller party*. type: Array<object Contact_>.
- ``buyer_party`` Required. *The buyer party of the invoice*.
- ``buyer_party[app_party_id]`` Required. *Party identifier of the third party application.* type: string. format: alphanumeric.
- ``buyer_party[type]`` Required. type: string. values: `'professional'` | `'institutional'` | `'individual'`.
- ``buyer_party[company]`` Required if type is `professional` (none otherwise). *The company of the buyer party*. type: object Company_.
- ``buyer_party[contacts]`` Required if type is `professional` (none otherwise). *Administrative contacts of the buyer party*. type: Array<object Contact_>.
- ``buyer_party[person]`` Required if type is `individual` (none otherwise). type: object Person_.
- ``delivery_address`` Optional. *Invoice's Delivery Address.* type: object Address_.
- ``reference`` Required. *Invoice reference number.* type: string. format: alphanumeric.
- ``description`` Optional. *Invoice description.* type: string. format: alphanumeric.
- ``issue_date`` Required. type: string. format: date.
- ``invoice_type_code`` Required. *Type of the invoice*. type: char. value:s `'S'` (standard) | `'C'` (credit note).
- ``currency_code`` Required. *Currency used in invoice format*. type: string. format: 3 digits as defined by [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html).
- ``taxes`` Optional. *An array of taxes with a different rate for the invoice*.
- ``total`` Required. *Total amount of the invoice before taxes*. type: decimal. 
- ``total_taxes`` Required. *Taxes amount of the invoice*. type: decimal.
- ``total_due`` Required. *Total amount of the invoice including taxes*. type: decimal.
- ``terms``: Optional. *List of terms. See JSON example for available fields*. type: Array<Dict>.
- ``lines`` Required. *Invoice lines*. type: Array<object InvoiceLine_>.
- ``journal_entries`` Optional. *Invoice's journal entries*. type: Array<object JournalEntry_>.
- ``notes``: Optional. *Free text.* type: string.

.. _InvoiceLine:

InvoiceLine
-----------

**Structure**


.. code-block:: json

	{
		"description": "Food",
		"taxes": [
			{
				"tax_rate": 5.5,
				"total": 20,
				"total_taxes": 1.1,
				"total_due": 21.1
			},
			{
				"tax_rate": 19.6,
				"total": 10,
				"total_taxes": 1.96,
				"total_due": 11.96
			}
		],
		"total": 30,
		"total_taxes": 2.07,
		"total_due": 32.07,
		"items": []
	}

**Attributes**


- ``description`` Optional. *Free form text*. type: string. format: alphanumeric. 
- ``taxes`` Optional. *An array of taxes with a different rate for the invoice*.
- ``total`` Required. *Total amount of the invoice line before taxes*. type: decimal.
- ``taxes`` Required. *Taxes amount of the invoice line*. type: decimal.
- ``total_due`` Required. *Total amount of the invoice line including taxes*. type: decimal. 
- ``items`` Required. *Line items*. type: Array<object InvoiceLineItem_>

.. _InvoiceLineItem:

InvoiceLineItem
---------------

**Structure**

.. code-block:: json

	{
		"lot_id": "ABCDE12345",
		"description": "Beef steak",
		"quantity": 12.5,
		"unit": "kg",
		"unit_price": 4,
		"total": 50,
		"tax_rate": 5.5,
		"total_taxes": 2.75,
		"total_due": 52.75,
		"journal_entries": []
	}

**Attributes**

- ``lot_id`` Optional. *Item's lot identification number*. type: string. format: alphanumeric
- ``description`` Required. type: string. format: alphanumeric. 
- ``quantity`` Optional. type: decimal. 
- ``unit`` Optional. type: string. format: alphanumeric
- ``unit_price`` Optional. type: decimal. 
- ``total`` Required. *Total amount of the invoice line item before taxes*. type: decimal.
- ``total_taxes`` Required. *Taxes amount of the invoice line item*. type: decimal. 
- ``total_due`` Required. *Total amount of the invoice line item including taxes*. type: decimal. 
- ``journal_entries`` Optional. *Item's journal entries*. type: Array<object JournalEntry_>.

.. _JournalEntry:

JournalEntry
------------


**Structure**

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

- ``app_journal_id`` Optional. *Journal ID of the accounting journal*. type: string. format: alphanumeric.
- ``journal_code`` Optional. *Journal code of the accounting journal*. type: string. format: alphanumeric.
- ``journal_description`` Optional. *Journal description of the accounting journal*. type: string. format: alphanumeric.
- ``account_number`` Required. *Account number for the accounting entry*. type: string. format: alphanumeric.
- ``account_description`` Optional. *Account description*. type: string. format: alphanumeric
- ``debit`` Required. *Debit amount*. type: decimal
- ``credit`` Required. *Credit amount*. type: decimal

.. _Person:

Person
-------

**Structure**


.. code-block:: json

	{
		"name": "John Doe",
		"email": "john.doe@gmail.com",
		"phone": "+33601010101",
		"address": { }
	}

**Attributes**

- ``name`` Required. *Name of the person*. type: string. format: alpha.
- ``email`` Required. *Email of the person*. type: string. format: valid email.
- ``phone`` Optional. *Phone number of the person*. type: string. format: valid phone number as defined by E.164, the international public telecommunication numbering plan.
- ``address`` Optional. *Address of the person*. type: object Address_.
