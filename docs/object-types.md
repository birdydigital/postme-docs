## Address

JSON Object example

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

## Contact

JSON Object example

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
