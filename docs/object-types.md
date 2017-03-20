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

- __`country_code`__ : *Country code of the address*. type: string. format: 2 digits As defined by the ISO 3166-1 alpha-2.

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
