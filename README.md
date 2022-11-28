# python-lib cookiecutter template

Cookiecutter template for creating a new Python library

Use this template on your own machine with cookiecutter.

## Installation

You'll need to have [cookiecutter](https://cookiecutter.readthedocs.io/) installed:

    brew install cookiecutter

## Usage

Run `cookiecutter gh:msleigh/python-lib` and then answer the prompts. Here's an example run:

    $ cookiecutter gh:msleigh/python-lib
    lib_name []: python lib template demo
    description []: Demonstrating https://github.com/msleigh/python-lib
    hyphenated [python-lib-template-demo]:
    underscored [python_lib_template_demo]:
    github_username []: msleigh
    author_name []: msleigh

I strongly recommend accepting the suggested value for "hyphenated" and "underscored" by hitting enter on those prompts.
This will create a directory called `python-lib-template-demo` - the name you enter is converted to lowercase and uses hyphens instead of spaces.

## Developing your library

Having created the new structure from the template, here's how to start working on the library.

    cd python-lib-template-demo
    # Create and activate a virtual environment:
    python3 -mvenv .venv
    source .venv/bin/activate
    # Install with dependencies so you can edit the project:
    pip install -e '.[dev,docs,tests]'

You can run the default test for your library like so:

    pytest

This will execute the test in `tests/test_python_lib_template_demo.py`.

Build the Sphinx documentation with:

    make -C docs html

Format Python code:

    black .

## Creating a Git repository for your library

You can initialize a Git repository for your library like this:

    cd python-lib-template-demo
    git init
    git add .
    git commit -m "Initial structure from template"

## Publishing your library to GitHub

Use https://github.com/new to create a new GitHub repository sharing the same name as your library, which should be something like `python-lib-template-demo`.

Push your `main` branch to GitHub like this:

    git remote add origin https://msleigh@github.com/msleigh/python-lib-template-demo.git
    git push -u origin main

The template will have created a GitHub Action which runs your library's test suite against every commit.

## Publishing your library as a package to PyPI

The template also includes an Action for publishing packages to [PyPI](https://pypi.org/).

To use this action, you need to create a PyPI account and an API token against that account.

Once you have created your account, navigate to https://pypi.org/manage/account/token/ and create an API token. For initial publication of the package you will need to set the scope of the token to "Entire account (all projects)".

Add that token to your repository as a GitHub secret called `PYPI_TOKEN`. You can find this in the "Settings -> Secrets -> Actions -> New Secret" area of the repository. The token should begin with the string `pypi-`.

Now, any time you create a new "Release" on GitHub the Action will build your package and push it to PyPI. The tag for the new release needs to match the `VERSION` string at the top of your `setup.py` file.

After the first release has gone out you can create a new PyPI API token that is scoped just to that project and use that to replace the `PYPI_TOKEN` secret in your GitHub repository settings.

## Attribution

Adapted from [python-lib cookiecutter template](https://github.com/simonw/python-lib).
