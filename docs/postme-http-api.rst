.. _postme-http-api:

Postme HTTP API
===============


Companies
---------

.. http:post:: /api/company
   
   Push a new company.

   **Example request**:

   .. sourcecode:: http

      POST /api/company HTTP/1.1
      Host: example.com
      Accept: application/json
      
      {
         "name": "My Organization",
         "address":  {
            "address_1": "456 Street Name",
            "address_2": "",
            "postal_code": "69003",
            "city": "Lyon",
            "country_code": "FR"
         },
         "identification": {
            "siren_id": "654654654",
            "vat_id":   "FR27654654654",
            "siret_id": "65465465400045"
         }
      }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 201 Created
      Vary: Accept
      Content-Type: application/json

   :reqheader Accept: ``application/json``
   :reqheader Authorization: ``Bearer [TOKEN]``
   :resheader Content-Type: ``application/json``
   :statuscode 201: Company created
   :statuscode 401: Invalid Authorization Token
   :statuscode 400: Invalid params


Invoices
--------

.. http:post:: /api/invoices

   Push a new invoice.

   **Example request**:

   .. sourcecode:: http

      POST /api/invoices HTTP/1.1
      Host: example.com
      Accept: application/json

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 202 Accepted
      Vary: Accept
      Content-Type: application/json

   :jsonparam `object-invoice` invoice: the invoice
   :reqheader Accept: ``application/json``
   :reqheader Authorization: ``Bearer [TOKEN]``
   :resheader Content-Type: ``application/json``
   :statuscode 202: Invoice successfully sent to postme
   :statuscode 401: Invalid Authorization Token
   :statuscode 400: Invalid params


Parties
------

.. http:post:: /api/parties
   
   Push a new party.

   **Example request**:

   .. sourcecode:: http

      POST /api/parties HTTP/1.1
      Host: example.com
      Accept: application/json
      
      {
         "app_party_id": "456456",
         "app_reference": "CUSTOMER-145"
         "type": "individual",
         "person": {
            "name": "John Doe",
            "email": "john.doe@gmail.com",
            "phone": "+33601010101",
            "address": { }
         }
      }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 201 Created
      Vary: Accept
      Content-Type: application/json

   :reqheader Accept: ``application/json``
   :reqheader Authorization: ``Bearer [TOKEN]``
   :resheader Content-Type: ``application/json``
   :statuscode 201: Party created
   :statuscode 401: Invalid Authorization Token
   :statuscode 400: Invalid params

.. http:get:: /api/parties/{app_party_id}
   
   Get the party with the APP ID ``app_party_id``.

   **Example request**:

   .. sourcecode:: http

      GET /api/parties/fd4g654s654df65s4f6s5 HTTP/1.1
      Host: example.com

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

      {
         "app_party_id": "456456",
         "app_reference": "CUSTOMER-145"
         "type": "individual",
         "person": {
            "name": "John Doe",
            "email": "john.doe@gmail.com",
            "phone": "+33601010101",
            "address": { }
         }
      }

   :reqheader Authorization: ``Bearer [TOKEN]``
   :resheader Content-Type: ``application/json``
   :statuscode 201: Party created
   :statuscode 401: Invalid Authorization Token
   :statuscode 400: Invalid params

