# Web applications

This section lists some best practice for web applications.

## Django boilerplate

For new applications we have a [cookie cutter
template](https://github.com/uisautomation/django-boilerplate) which can be used
to implement new projects.

## REST API First

Start by designing the API for the application. Make sure that the API is
self-documenting by including a ``swagger.json`` schema document at the root of
the API.

## Use Django

We usually use the [Django](https://www.djangoproject.com/) web framework for
writing webapps. Occasionally we will use a lighter framework like
[Flask](http://flask.pocoo.org/) for tiny web services.

## Use Django REST framework

Since [our new applications are likely to have REST APIs](#rest-api-first) we
usually use the [Django REST Framework](https://www.django-rest-framework.org/)
to implement them.
