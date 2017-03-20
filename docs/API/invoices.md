# Send invoices

*Documentation in progress*

Before sending a new invoice, you need to make sure the invoice sender is already registered on postme.io.

If not, please visit "Register a new company" how-to section.

### Resource

|URL|`/api/invoices`|
|---|---|
|Method|POST|
|Headers|Authorization |
|JSON Request Body|Invoice object|


### Parameters

See InvoiceObject section.

Note: *All parameters prefixed with `app_` refer to the third party application data.*

### Response

__On success__

|Http status code|content|description|
|---|---|---|
|201||Success|

__On error__

|Http status code|content|description|
|---|---|---|
|401||Unauthorized|

Error codes:

|Error code|Meaning|
|---|---|
|11||
