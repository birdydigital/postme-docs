# Create a new company

Register a new company to enable it to send or receive invoices

__Resource__

|URL|`/api/companies`|
|---|---|
|Method|POST|
|Headers|Authorization |

__Request JSON payload example__


__Parameters__

- __`name`__ Required. *The name of the company*. type: string. format: alphanumeric.
- __`vat_id`__ Required. *VAT Identification Number of the company*. type: string. format: alphanumeric.
- __`siren_id`__ Required. *SIREN Identification Number of the company (for french companies only)*. type: string. format: numeric.
- __`address`__ Required. *Address of the company*. type: `Address` (please refer to the Object Types > Address section).
- __`contacts`__ Optional. *Contacts of the company*. type: `Array(Contact)`.