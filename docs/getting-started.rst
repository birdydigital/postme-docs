.. _getting-started:

Getting started
===============

Prerequisites
-------------

Create a developer account
~~~~~~~~~~~~~~~~~~~~~~~~~~

First thing you need to do is creating a developer account.

* Go to https://app.postme.io
* Click on "Create a developer account"
* Activate your email adress

Register your application
~~~~~~~~~~~~~~~~~~~~~~~~~

* From the dashboard, go to "My apps"
* Click on "New App"
* Enter a title for your app (i.e. "My invoicing system")
* Save


Generate your application credentials
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once your application is created, you can generate App ID/key pairs to get API access.

* Click on "Generate New Key"
* Enter a name for the new generated key (i.e. "Test")
* If you want to use these credentials for test purpose, check "Sandbox Mode"


Using Postme API
----------------

Authentication
~~~~~~~~~~~~~~

.. http:post:: /api/login

   **Example request**:

   .. sourcecode:: http

      POST /api/login HTTP/1.1
      Host: example.com
      Accept: application/json

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Vary: Accept
      Content-Type: application/json

   :jsonparam `string` app_id: your APP_ID
   :jsonparam `string` app_secret: your APP_SECRET
   :reqheader Accept: ``application/json``
   :resheader Content-Type: ``application/json``
   :statuscode 200: Authentication succeeded
   :statuscode 401: Wrong credentials

Root URL
~~~~~~~~

If you send an HTTP GET request to the Postme API Root URL e.g. `https://api.postme.io/api`, then you should get an HTTP response with something like the following in the body:

.. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

      {
            "_links" : {
              "api_v1": "https://api.postme.io/api/v1/",
              "docs": "https://docs.postme.io/",
              "..."
            },
            "third_application": {
                  "app_id": "5349162981239685"
            },
            "version": "0.1.0"
      }

(In Progress)

Root Endpoint
~~~~~~~~~~~~~

If you send an HTTP GET request to the Postme API Root Endpoint e.g. `https://api.postme.io/api/v1`, then you should get an HTTP response that allows you to discover the Postme API endpoints :

.. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

      {
            "_links" : {
              "self": "https://api.postme.io/api/v1/",
              "invoices": "https://api.postme.io/api/v1/invoices/",
              "..."
            }
      }


(In Progress)

Using Postchain
---------------

Create a new private/public keys
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Behaviour
~~~~~~~~~

.. image:: send_invoice_process.png