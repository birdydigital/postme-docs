.. _invoices:

Invoices
========

Send a new invoice
-------------

.. http:post:: /api/invoices

   **Example request**:

   .. sourcecode:: http

      POST /api/invoices HTTP/1.1
      Host: app.postme.io
      Accept: application/json, text/javascript

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 201 Created
      Vary: Accept
      Content-Type: application/json

   :jsonparam `object-invoice` invoice: the invoice
   :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
   :reqheader Authorization: Bearer
   :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request
   :statuscode 201: no error
   :statuscode 401: Unauthorized