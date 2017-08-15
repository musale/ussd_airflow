.. _tutorial:


=====================
Creating USSD screens
=====================

This document is a whirlwind tour of how to create USSD screen.

Strong feature of USSD airflow is to create USSD screen via ``yaml`` and not
directly in code. This makes it easier to give the product owners to design
USSD without knowing how to code

In USSD airflow, the customer journey is created via ``yaml``.
Each section in the ``yaml`` file defines a USSD screen.
There different types of USSD and each type has its own rule on how
to write USSD application.

Common rule in creating any kind of screen
**Each screen has field called "type"** apart from initial_screen

The following are types of USSD and the rules to write them.

1. Initial screen (type -> initial_screen)
------------------------------------------

.. automodule:: ussd.screens.initial_screen
    :members: InitialScreen

2. Input screen (type -> input_screen)
--------------------------------------

.. automodule:: ussd.screens.input_screen
   :members: InputScreen

3. Menu screen (type -> menu_screen)
------------------------------------

.. autoclass:: ussd.screens.menu_screen.MenuScreen


4. Quit screen (type -> quit_screen)
------------------------------------

.. autoclass:: ussd.screens.quit_screen.QuitScreen


5. Http screen (type -> http_screen)
------------------------------------

.. autoclass:: ussd.screens.http_screen.HttpScreen

6. Router screen (type -> router_screen)
----------------------------------------

.. autoclass:: ussd.screens.router_screen.RouterScreen

7. Update session screen (type -> update_session_screen)
--------------------------------------------------------

.. autoclass:: ussd.screens.update_session_screen.UpdateSessionScreen

8. Custom screen (type -> custom_screen)
----------------------------------------

.. autoclass:: ussd.screens.custom_screen.CustomScreen


***Once you have created your ussd screens run the following code to validate
them:***

   .. code-block:: text

         python manage.py validate_ussd_journey /path/to/your/ussd/file.yaml
