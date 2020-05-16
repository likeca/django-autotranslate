
django-autotranslate
====================

A simple Django app to automatically translate the pot (`.po`) files generated by django's makemessages command
using google translate.

[![][travis-ci]][travis] [![][pypi-version]][pypi] ![][requirements]

Installation:
-------------

```bash
    pip install django-autotranslate
```

Add ``'autotranslate'`` to your ``INSTALLED_APPS`` setting.

```python
    INSTALLED_APPS = (
        ...
        'autotranslate',
    )
```

Quickstart:
-----------

```bash
    python manage.py translate_messages
```

The command finds all the generated pot (``.po``) files under the locale paths (``LOCALE_PATHS``) specified in django project settings, and translates them automatically.


Options:
--------

- ``-f, --set-fuzzy``: Set the 'fuzzy' flag on autotranslated entries
- ``-l, --locale 'locale'``: Only translate the specified locales
- ``-u, --untranslated``: Only translate the untranslated messages

```bash
    python manage.py translate_messages -l 'de' -l 'es'
```

Settings:
---------

- Use a different Translation Service:

```python
    # default: 'autotranslate.services.GoSlateTranslatorService'
    # pip install google-api-python-client
    AUTOTRANSLATE_TRANSLATOR_SERVICE = 'autotranslate.services.GoogleAPITranslatorService'
    GOOGLE_TRANSLATE_KEY = '<google-api-key>'
```

Compatibility Matrix:
--------------------

| autotranslate | django      |
| :-----------: | :---------: |
| v1.0.x        | Django 1.5+ |
| v1.1.x        | Django 1.8+ |

    
- Use Azure Translator Text (Global Region)
Create Azure Translator Text managed service in Global Region.
```
    AUTOTRANSLATE_TRANSLATOR_SERVICE = 'autotranslate.services.GoogleWebTranslatorService'
    AZURE_TRANSLATOR_SECRET_KEY='<Azure Tranxlator Text Secret Key>'
```

- Use GoogleWebTranslatorService
```
    AUTOTRANSLATE_TRANSLATOR_SERVICE = 'autotranslate.services.GoogleWebTranslatorService'
```

Tests:
-----

```bash
    # run test against all environments
    tox
    # run test against a specific environment defined in tox.ini
    # eg. django>1.9 & python3.4
    tox -e dj19-py34
```

[travis-ci]: https://travis-ci.org/ankitpopli1891/django-autotranslate.svg?branch=master
[travis]: https://travis-ci.org/ankitpopli1891/django-autotranslate

[pypi-version]: https://img.shields.io/pypi/v/django-autotranslate.svg
[pypi]: https://pypi.python.org/pypi/django-autotranslate/

[requirements]: https://requires.io/github/ankitpopli1891/django-autotranslate/requirements.svg?branch=master
