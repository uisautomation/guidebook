# Python

The DevOps division are heavy users of the Python programming language
for backend work.

## Code style

We do not maintain a style guide but [Google's
guide](https://github.com/google/styleguide/blob/gh-pages/pyguide.md) is a good
starting point.

## flake8

Most of our Python code is set up to automatically check Python code for PEP8
compliance. We use the default set of rules for flake8 except that we relax the
maximum line length to 99 characters. (This being the maximum allowed by PEP8.)

## Testing

Use unit testing to check functionality of code. Sometimes, the use of
[doctest](https://docs.python.org/3/library/doctest.html) is useful for
functions which are private to a module. Generally, we use the Django test
runner provided by the boilerplate application.

## Code coverage

Test code coverage is reported in most of our code and a minimal code coverage
level is enforced for most of our repositories. New code should usually be
accompanied by tests which exercise the code.
