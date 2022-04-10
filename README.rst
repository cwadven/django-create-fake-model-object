================================
Django Create Fake Model Object
================================

Django Create Fake Model Object is a Django app to make random fake data
It also creates Foreign objects and M2M objects!


Quick Start
============

1. Add "create_fake_model_object" to your INSTALLED_APPS setting like this::

    INSTALLED_APPS = [
        ...,
        'create_fake_model_object',
    ]


2. If you want to create a new model object use the following command to create.::

    python manage.py createrandom (appname) (Modelname) (option -n createnumber)

    # Example
    python manage.py createrandom book Book -n 7

