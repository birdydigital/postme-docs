.. _invoices:

Invoices
========

Send a new invoice
------------------

.. http:post:: /api/invoices

   **Example request**:

   .. sourcecode:: http

      POST /api/invoices HTTP/1.1
      Host: app.postme.io
      Accept: application/json

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 Success
      Vary: Accept
      Content-Type: application/json

   :jsonparam `object-invoice` invoice: the invoice
   :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
   :reqheader Authorization: Bearer [TOKEN]
   :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request
   :statuscode 200: No error
   :statuscode 401: Unauthorized
   :statuscode 400: Bad request


Retrieve invoices
-----------------


