.. _starting:


===============
Getting started
===============

This section walks you through the basic setup for USSD Airflow

Installation and setup
----------------------

- Run the following command to install using ``pip``

  .. code-block:: text

    $ pip install ussd_airflow

- Add **ussd_airflow** in ``INSTALLED_APPS``

  .. code-block:: python

    INSTALLED_APPS = [
      'ussd.apps.UssdConfig',
    ]

- Change the session serializer to ``pickle serializer``

  .. code-block:: python

    SESSION_SERIALIZER = 'django.contrib.sessions.serializers.PickleSerializer'

Using the default view
------------------

A default view has been implemented to handle AfricasTalking USSD gateway.

To use it with your own USSD screen, create a ``yaml`` file with your ussd screen.

.. note::
  Learn more on how to create ussd screen here :doc:`tutorial`.

For quick start, use the ``yaml`` file below:

  .. literalinclude:: .././ussd/tests/sample_screen_definition/sample_customer_journey.yml


Next, add the path to your USSD screen ``yaml`` file in the ``settings.py``.

  .. code-block:: python

    DEFAULT_USSD_SCREEN_JOURNEY = "/yaml/file/path"

  .. tip::
    To validate your ussd screen file. Run this command

    .. code-block:: text

      $ python manage.py validate_ussd_journey /yaml/file/path

    To test the ussd view do this curl request.

    .. code-block:: bash

      $ curl -X POST -H "Content-Type: application/json" \
        -H "Cache-Control: no-cache" \
        -H "Postman-Token: 3e3f3fb9-99b9-b47d-a358-618900d486c6" \
        -d '{"phoneNumber": "400","sessionId": "105","text":"1", \
        "serviceCode": "312"}' \
        "http://{your_host}/{you_path}/africastalking_gateway"

Writing a custom view
---------------------
Creating a custom view is easy.

- Inherit from ``ussd.core.UssdView`` (Mandatory)

- Define ``HTTP`` method either ``GET`` or ``POST`` (Mandatory)
  The http method should return ``ussd.core.UssdRequest``

- Define the variable ``customer_journey_conf``. This is the path of the file that has USSD screens. If you want your file to be dynamic implement the ``get_customer_journey_conf`` method. This method is called by the request object.

- Define the ``customer_journey_namespace`` variable. ``Ussd_airflow`` uses this namespace to save the customer journey content in memory. If you want ``customer_journey_namespace`` to be dynamic implement the ``get_customer_journey_namespace`` method. This method is called by the request object.

- Lastly, override ``HttpResponse``. In USSD airflow the ``HTTP`` methods return a ``core.ussd.UssdRequest`` object and not ``HTTP`` response. Then the ``USSD`` view gets the ``UssdResponse`` object and converts it to ``HttpResponse``. The default ``HttpResponse`` returned is a normal ``HttpResponse`` with body being the ``USSD`` text.

  .. tip::
    To override ``HttpResponse`` returned define a ``ussd_response_handler`` method which will be called with ``UssdResponse`` object.

Example of a custom ``UssdView``
-------------------------------

  .. code-block:: python

      from ussd.core import UssdView, UssdRequest


      class SampleOne(UssdView):

          def get(self, req):
              return UssdRequest(
                  phone_number=req.data['phoneNumber'].strip('+'),
                  session_id=req.data['sessionId'],
                  ussd_input=text,
                  service_code=req.data['serviceCode'],
                  language=req.data.get('language', 'en')
              )

Example of custom ``UssdView`` that defines its own ``HttpResponse``
-------------------------------------------------------------------

  .. code-block:: python

      from ussd.core import UssdView, UssdRequest


      class SampleOne(UssdView):

          def get(self, req):
              return UssdRequest(
                  phone_number=req.data['phoneNumber'].strip('+'),
                  session_id=req.data['sessionId'],
                  ussd_input=text,
                  service_code=req.data['serviceCode'],
                  language=req.data.get('language', 'en')
              )

          def ussd_response_handler(self, ussd_response):
              if ussd_response.status:
                  res = 'CON' + ' ' + str(ussd_response)
                  response = HttpResponse(res)
              else:
                  res = 'END' + ' ' + str(ussd_response)
                  response = HttpResponse(res)
              return response

Example application
-------------------

Looking for some example application?  We provide the following example
application to get you up and running quickly.  They show you how to setup
Stormpath, and implement a profile page for the logged-in user:

  - `USSD Airflow Example Project`_

  .. _USSD:https://github.com/mwaaas/ussd_airflow/tree/master/ussd_airflow_app_tpl
