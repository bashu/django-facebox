django-facebox
==============

This is a [Django](https://www.djangoproject.com/) integration of [Facebox](http://defunkt.io/facebox/).

Authored by [Basil Shubin](https://github.com/bashu)

[![Latest Version](https://img.shields.io/pypi/v/django-facebox.svg)](https://pypi.python.org/pypi/django-facebox/)
[![Downloads](https://img.shields.io/pypi/dm/django-facebox.svg)](https://pypi.python.org/pypi/django-facebox/)
[![License](https://img.shields.io/github/license/bashu/django-facebox.svg)](https://pypi.python.org/pypi/django-facebox/)

## Installation

    $ pip install django-facebox

### External dependencies

* jQuery - This is not included in the package since it is expected that in most scenarios this would already be available.

## Setup

Add `facebox` to  `INSTALLED_APPS`:
```python
INSTALLED_APPS = [
	...
	'facebox',
]
```
Be sure you have the `django.core.context_processors.request` processor
```python
TEMPLATE_CONTEXT_PROCESSORS = [
	...
	"django.core.context_processors.request",
]
```
and just include `facebox` templates
```html
{% include "facebox/facebox_css.html" %} {# Before the closing head tag #}
{% include "facebox/facebox_js.html" %} %} {# Before the closing body tag #}
```
When deploying on production server, don't forget to run :
```shell
$ python manage.py collectstatic
```
## Usage

Extend base template for ajax requests
```html
{% extends request.is_ajax|yesno:"facebox/base.html,base.html" %}
```
Add `rel="facebox"` to a link, and set the href to a page you want to display
```html
<a href="{% url 'remote.html' %}" rel="facebox">Click here</a>
```
Please see `example` application. This application is used to manually test the functionalities of this package. This also serves as a good example.

You need only Django 1.4 or above to run that. It might run on older versions but that is not tested.

## License

`django-facebox` is released under the BSD license.
