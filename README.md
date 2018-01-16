pylint-django
=============

[![Build Status](https://travis-ci.org/MrSenko/django-pylint.svg?branch=master)](https://travis-ci.org/MrSenko/django-pylint)
[![Coverage Status](https://coveralls.io/repos/MrSenko/django-pylint/badge.svg)](https://coveralls.io/r/MrSenko/django-pylint)

# About

`django-pylint` is a [Pylint](http://pylint.org) plugin for improving code analysis
for when analysing code using Django. This package is a currently maintained fork of
[pylint-django](https://github.com/landscapeio/pylint-django)!

## Usage

#### Pylint

Ensure `django-pylint` is installed and on your path (`pip install django-pylint`), and then run pylint:

```
pylint --load-plugins pylint_django [..other options..]
```

# Features

* Prevents warnings about Django-generated attributes such as `Model.objects` or `Views.request`.
* Prevents warnings when using `ForeignKey` attributes ("Instance of ForeignKey has no <x> member").
* Fixes pylint's knowledge of the types of Model and Form field attributes
* Validates `Model.__unicode__` methods.
* `Meta` informational classes on forms and models do not generate errors.

# Contributing

Please feel free to add your name to the `CONTRIBUTORS.md` file if you want to be
credited when pull requests get merged. You can also add to the `CHANGELOG.md` file.

## Tests

The structure of the test package follows that from pylint itself.

It is fairly simple: create a module starting with `func_` followed by
a test name, and insert into it some code. The tests will run pylint
against these modules. If the idea is that no messages now occur, then
that is fine, just check to see if it works by running `scripts/test.sh`.

Ideally, add some pylint error suppression messages to the file to prevent
spurious warnings, since these are all tiny little modules not designed to
do anything so there's no need to be perfect.

It is possible to make tests with expected error output, for example, if
adding a new message or simply accepting that pylint is supposed to warn.
Add a `.txt` file which should match the name of the test and contains
error type, line number, class and expected text. The test code itself
should also be annotated with comments on lines which are supposed to
trigger pylint messages! See `func_model_does_not_use_unicode_py33`
for example!


# License

`django-pylint` is available under the GPLv2 license.
