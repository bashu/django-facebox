Django-Facebox
==============

This is a [Django](https://www.djangoproject.com/) integration of [Facebox](http://defunkt.io/facebox/).

[![Latest Release](https://pypip.in/py/django-facebox/badge.png)](http://badge.fury.io/py/django-facebox) [![Downloads](https://pypip.in/py/django-facebox/badge.png)](https://crate.io/packages/django-facebox?version=latest)

## Installation

    $ pip install django-facebox

### External dependencies

* jQuery - This is not included in the package since it is expected that in most scenarios this would already be available.

## Setup

Add `facebox` to  `INSTALLED_APPS`:

    INSTALLED_APPS = [
		...
    	'facebox',
	]

Be sure you have the `django.core.context_processors.request` processor

	TEMPLATE_CONTEXT_PROCESSORS = [
		..
    	"django.core.context_processors.request"
	]

and just include `facebox` templates

    {% include "facebox/facebox_css.html" %} {# Before the closing head tag #}
	{% include "facebox/facebox_js.html" %} %} {# Before the closing body tag #}

When deploying on production server, don't forget to run :

    $ python manage.py collectstatic

## Usage

Extend base template for ajax requests

    {% extends request.is_ajax|yesno:"facebox/base.html,base.html" %}

Add `rel="facebox"` to a link, and set the href to a page you want to display

    <a href="{% url 'remote.html' %}" rel="facebox">Click here</a>

Please see `example` application. This application is used to manually test the functionalities of this package. This also serves as a good example.

You need only Django 1.4 or above to run that. It might run on older versions but that is not tested.

## License

`django-facebox` is released under the BSD license.
