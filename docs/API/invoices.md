# Send invoices

*Documentation in progress*


### Call

|URL|/api/invoices|
|:---|---|
|Method|POST|

### Response

#### On Success

|Http status code|Content|Description|
|:---|---|---|
|201||

#### On Error

|Http status code|Content|Description|
|:---|---|---|
|401||

__ Request payload __


---

__Parameters__

*All parameters prefixed with `app_` refer to the third party application data.*

__Required params__

__Invoice__

- `app_invoice_id`: Invoice identifier of the third party application.
- `sender`: type COMPANY
- `receiver`: type CONTACT|COMPANY
- `receiver_type`: 'professional' | 'institutional' | 'individual'
- `reference`: Reference of the invoice.
- `issue_date`: 
- `invoice_type_code`:
- `currency_code`
- `total`: Total amount before taxes
- `total_due`: Total amount including taxes
- `taxes`: Taxes amount
- `lines`: Invoice lines
- `terms`: {due_date}
- TODO: add compta

__Invoice Line__

- `total`: total HT
- `taxes`
- `items`

__Invoice Line Item__

- `lot_id`
- `description`
- `quantity`
- `unit_price`
- `unit`
- `total`
- `taxes`
- `accounting_entries`

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
