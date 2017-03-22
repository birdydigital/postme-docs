.. _getting-started:

Getting started
===============

Access and API keys
-------------------

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

Generate a key
~~~~~~~~~~~~~~

Once your application is created, you can generate App ID/key pairs to get API access.

* Click on "Generate New Key"
* Enter a name for the new generated key (i.e. "Test")
* If you want to use these credentials for test purpose, check "Sandbox Mode"


API Authentication
------------------

.. http:post:: /api/login

   **Example request**:

   .. sourcecode:: http

      POST /api/login HTTP/1.1
      Host: app.postme.io
      Accept: application/json

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200
      Vary: Accept
      Content-Type: application/json

   :jsonparam `string` _username: APP_ID
   :jsonparam `string` _password: APP_SECRET
   :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
   :reqheader Authorization: Bearer
   :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request
   :statuscode 200: No error
   :statuscode 401: Unauthorized
