django-facebox
==============

This is a Django_ integration of Facebox_.

.. image:: https://img.shields.io/pypi/v/django-facebox.svg
    :target: https://pypi.python.org/pypi/django-facebox/

.. image:: https://img.shields.io/pypi/dm/django-facebox.svg
    :target: https://pypi.python.org/pypi/django-facebox/

.. image:: https://img.shields.io/github/license/bashu/django-facebox.svg
    :target: https://pypi.python.org/pypi/django-facebox/

Installation
------------

.. code-block:: shell

    pip install django-facebox
    
External dependencies
~~~~~~~~~~~~~~~~~~~~~

* jQuery - This is not included in the package since it is expected that in most scenarios this would already be available.

Setup
-----

Add ``facebox`` to  ``INSTALLED_APPS``:

.. code-block:: python

    INSTALLED_APPS += (
        'facebox',
    )

Be sure you have the ``django.template.context_processors.request`` processor

.. code-block:: python

    TEMPLATES = [
        {
            ...
            'OPTIONS': {
                'context_processors': [
                    ...
                    'django.template.context_processors.request',
                ],
            },
        },
    ]

and just include ``facebox`` templates

.. code-block:: html+django

    {% include "facebox/facebox_css.html" %} {# Before the closing head tag #}
    {% include "facebox/facebox_js.html" %} {# Before the closing body tag #}

When deploying on production server, don't forget to run :

.. code-block:: shell

    python manage.py collectstatic

Usage
-----

Extend base template for ajax requests

.. code-block:: html+django

    {% extends request.is_ajax|yesno:"facebox/base.html,base.html" %}

Add ``rel="facebox"`` to a link, and set the href to a page you want to display

.. code-block:: html+django

    <a href="{% url 'remote.html' %}" rel="facebox">Click here</a>

Please see ``example`` application. This application is used to manually test the functionalities of this package. This also serves as a good example.

You need only Django 1.4 or above to run that. It might run on older versions but that is not tested.

License
-------

``django-facebox`` is released under the BSD license.

.. _django: https://www.djangoproject.com/
.. _facebox: http://defunkt.io/facebox/
