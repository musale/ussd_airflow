.. _change_log:


======================
USSD Airflow Changelog
======================

All library changes, in descending order.

Version 0.0.4.6
-----------------
Feature
    - Allow Content Provider to determine language to use to display screens

Version 0.0.4.5
-----------------
fix-bug
    - fixing bug validation command failing if inheritance has been used

Version 0.0.4.4
-----------------
feature
    - next screen can now have routing options

Version 0.0.4.3
-----------------
enhancement
    - make request to use jinja2 evaluation

Version 0.0.4.2
-----------------
Feature
    - adding option for adding built in function

Version 0.0.4.1
-----------------
Enhancement
    - changed to convert datetime to string before saving it to session

Version 0.0.4
-----------------
Feature
    - adding option for report session

Version 0.0.3.9.1
-----------------
Enhancement
    - pagination options to be defined on customer journey

Version 0.0.3.9
---------------
Feature
    - adding built in option for session management

Version 0.0.3.8
---------------
Feature
    - adding custom handler support
    - adding pagination in menu screen still experimental

Version 0.0.3.7
---------------
Bug fix
    - error as a result of copying unsave variable

Version 0.0.3.6
---------------
Bug fix
    - error as a result of copying unsave variable

Version 0.0.3.5
---------------
Bug fix
    - loading variable template failing on some instance

Version 0.0.3.4
---------------

Feature
    - added recording screen interactions in the session

Version 0.0.3.3
---------------

Feature
    - refactored initial_screen to be able to
      support session variable assignment

Version 0.0.3.2
---------------
Feature
    - add screen that can save something in the session.

Version 0.0.3.1
---------------
Feature
    - added inheritance support on ussd customer journey

Version 0.0.3
---------------
Bug fix
    - http screen with non json response failing.

Version 0.0.2.9
---------------
Feature
    - http screen to support none json response
    - added django command for creating new ussd application

Version 0.0.2.8
---------------
Feature
    - initial support for custom filters
    - added built in date filters

Version 0.0.2.7
---------------
Enhancement
    - refactored the logic for evaluating jinja template

Version 0.0.2.6
---------------
Enhancement
    - removed url validation in http screen.
        This is to enable url can be a variable

Version 0.0.2.5
---------------
Enhancement
    - Support for using os variable in ussd template

Version 0.0.2.4
---------------
Bugfix
    - fixed backward incompatibility introduced by previous version
      in http_screen.

Version 0.0.2.3
---------------
Enhancement
    - http screen should save status_code and content

Version 0.0.2.2
---------------
Enhancement
    - improved variable declaration in yaml can now be nested


Version 0.0.2
-----------------

Feature
    - added support for defining variable files
    - added support for loop in router screen

Version 0.0.1.9.9
-----------------

Feature
    - ussd screens path can be relative

Version 0.0.1.9.8
-----------------

Bug fix
    - fixed sample customer journey


Version 0.0.1.9.7
-----------------

Bug fix
    - Sample view using invalid sample ussd conf

Version 0.0.1.9.6
-----------------

Bug fix
    - adding sample screens in the package

Version 0.0.1.9.5
-----------------

Bug fix
    - adding missing package 'yaml' in the dependencies list.

Version 0.0.1.9.4
-----------------

Bug fix
    - adding missing package 'yaml' in the dependencies list.


Version 0.0.1.9.3
-----------------

Bug fix
    - adding missing package 'celery' in the dependencies list.


Version 0.0.1.9.2
-----------------

Bug fix
    - adding missing package 'requests' in the dependencies list.

Version 0.0.1.9.1
-----------------

Bug fix
    - previous version fails when installing


Version 0.0.1.9
-----------------

Bug fix
    - previous version fails when installing


Version 0.0.1.8
-----------------

Feature
    - Adding feature when installing this package to install
      the packages it depends on.


Version 0.0.1.7
-----------------

BugFix
- if validation in input screen is missing proceed don't fail


Version 0.0.1.6
----------------
Enhancement
- validate_ussd_journey command to fail if customer journey fails validation




Version 0.0.1.5
----------------
Released on 15th Jan 2017

Feature
- adding django command to validate ussd customer journey

Enhancement
- increased ussd maximum text to 500
