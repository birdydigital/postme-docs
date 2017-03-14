# Send invoices

*Documentation in progress*


|URL|/api/invoices|
|---|---|
|method|POST|


__Parameters__

|Name|Type|Format|Required|Values|Default|Description|Comment|
|---|---|---|---|---|---|---|---|
|pif_version|string|decimal|0..1|"0.1"|latest|PIF version||
|internal_id|string|AN|1..1||~|Internal invoice ID||
|notes|string|AN|0..*||~	|Custom free-form Invoice extra info not contained in other fields
|issue_date	string	|datetime	||0..1|	||	~|	Invoice creation date assigned by the creditor||
|invoice_type_code|	string	|A	|1..1|	"- ""S"": Standard - ""C"": Credit note"|	~	|Invoice type||
|currency_code	|string	|A|	1..1	|ISO4217	|~	|Code of currency used in document||
|payment_means	|PAYMENT_MEAN		||0..*		|||~|	List of accepted payment means
|lines	|INVOICE_LINE			||1..*			|
|code	|string	|A	|1..1	|"- ""CC"": Credit card - ""CHQ"": Cheque"|	~|	Code of the payment mean||
|INVOICE LINE|
|internal_id|	string	|AN	|1..1		||~	|Internal invoice line ID||
|notes|	string	|AN	|0..*		||~	|Custom free-form Invoice Line extra info not contained in other fields||
|quantity	|string	|decimal	|0..1	||	~	|Quantity||
|price|	string	|decimal	|1..1|		|~	|Total price of the invoice line||
|vat	|string	|decimal	|0..1		||~	|Total VAT of the invoice line||
|item|	INVOICE_LINE_ITEM		||0..*	|||		|Items on the invoice line||
|INVOICE_LINE_ITEM							|
|internal_id	|string	|AN	|1..1		||~|	internal item ID|
|description	|string	|AN	|	1..1	||	~|
|quantity	|string	decimal	FALSE	0..1		~	Quantity of items on the invoice line
|unit	|string	|AN	|0..1		||~	|Unit||
|price	|string	|decimal	|0..1|		|~	|Total price||
|vat	|string	|decimal	|0..1|		|~|	total VAT||
|lot_id	|string	|AN|		0..1		|~|	Lot Identification||
|CONTACT							|
|ID	|string	|AN	|1..1		||~|	Identification of the contact||
|name	|string	|AN	|1..1		||~	|Name of the contact||
|telephone|	string	|AN	|0..1		||~	|Telephone number of the contact||
|email	|string	|AN	|0..1		||~	|Email adress of the contact||
|notes	|string	|AN	|0..*		||~	|Custom free-form contact extra info not contained in other fields	||
|AGENCY							|
|ID	|string	|AN	|1..1	||~	|Identification of the agency||
|name	|string	|AN	|1..1		||~|	Name of the agency||
|vat_id	|string	|	||				||VAT Identification number||
|siret_id	|string	|||||	|				For French agencies only|
|apet_id	|string	|	|||||				For french agencies only|
|address	|ADDRESS|
|contact	|CONTACT|
|notes	|string	|AN	|0..*		||~	|Custom free-form agency extra info not contained in other fields||