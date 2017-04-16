.. _postme-http-api:

Postme HTTP API
===============

Send a new invoice
------------------

.. http:post:: /api/invoices

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


Retrieve invoices
-----------------

Companies
---------

.. http:post:: /api/company
   
   Push a new company.

   **Example request**:

   .. sourcecode:: http

      POST /api/company HTTP/1.1
      Host: example.com
      Accept: application/json

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 201 Created
      Vary: Accept
      Content-Type: application/json

   :reqheader Accept: ``application/json``
   :reqheader Authorization: ``Bearer [TOKEN]``
   :resheader Content-Type: ``application/json``
   :statuscode 202: Invoice successfully sent to postme
   :statuscode 401: Invalid Authorization Token
   :statuscode 400: Invalid params

