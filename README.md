# python-lib cookiecutter template

Opinionated cookiecutter template for creating a new Python library

Use this template on your own machine with cookiecutter.

## Installation

You'll need to have [cookiecutter](https://cookiecutter.readthedocs.io/) installed. I recommend pipx for this:
```bash
pipx install cookiecutter
```
Regular `pip` will work OK too.

## Usage

Run `cookiecutter -o ~/projects gh:msleigh/python-lib` and then answer the prompts. Here's an example run:
```bash
cookiecutter -o ~/projects gh:msleigh/python-lib
```
```
lib_name []: python lib template demo
description []: Demonstrating https://github.com/msleigh/python-lib
hyphenated [python-lib-template-demo]:
underscored [python_lib_template_demo]:
github_username []: msleigh
author_name []: msleigh
```
I strongly recommend accepting the suggested value for "hyphenated" and "underscored" by hitting enter on those prompts.

This will create a directory called `~/projects/python-lib-template-demo` - the name you enter is converted to lowercase and uses hyphens instead of spaces.

See https://github.com/msleigh/python-lib-template-demo for the output of this example.

## Developing your library

Having created the new structure from the template, here's how to start working on the library.

The following dependencies are already included in the template's
`pyproject.toml` (as `dev` dependencies), so don't need to be added:

- black
- mkdocs-material
- pre-commit
- pytest
- ruff
- towncrier

If your library is called `my-new-library`, you can start working on it like so:
```bash
cd ~/projects/my-new-library
# Create a virtual environment and the `poetry.lock` file
poetry install
```
If you want to add any additional dependencies at this point, run:
```bash
poetry add ...
```

## Creating a Git repository for your library

You can initialize a Git repository for your library like this:
```bash
cd ~/projects/my-new-library
git init
git add .
git commit -m "Initial structure from template"
```

### Activate the virtual environment

This assumes your configuration of Poetry has the `virtualenvs.inproject`
variable set to `true` (not the default). (See the Poetry documentation.)
```bash
source .venv/bin/activate
```

You can run the default test for your library like so:
```bash
pytest
```
This will execute the test in `tests/test_my_new_library.py`.

### Build the documentation

Build the MkDocs documentation with:

    mkdocs build -f docs/mkdocs.yml -s

To start a deveopment server with live reloading to view the documentation:

    mkdocs serve -f docs/mkdocs.yml -s

which will also run the build.

### Format Python code

Run:

    black .

Commit any changes.

### Set up pre-commit

Run:

    pre-commit run --all-files

to check everything initially. Then:

    pre-commit autoupdate
    pre-commit install

Commit any changes.

## Publishing your library to GitHub

Use <https://github.com/new> to create a new GitHub repository sharing the same name as your library, which should be something like `my-new-library`.

Push your `main` branch to GitHub like this:
```bash
git remote add origin git@github.com:msleigh/my-new-library.git
git push -u origin main
```
The template will have created a GitHub Action which runs your library's test suite against every commit.

## Publishing your library as a package to PyPI

The template also includes a `publish.yml` GitHub Actions workflow for publishing packages to [PyPI](https://pypi.org/), using [pypa/gh-action-pypi-publish](https://github.com/pypa/gh-action-pypi-publish).

To use this action, you need to create a PyPI account and an API token against that account.

Once you have created your account, navigate to <https://pypi.org/manage/account/token/> and create an API token. For initial publication of the package you will need to set the scope of the token to "Entire account (all projects)".

Add that token to your repository as a GitHub secret called `PYPI_TOKEN`. You can find this in the "Settings -> Secrets -> New Secret" area of the repository. The token should begin with the string `pypi-`.

Now, any time you create a new "Release" on GitHub the Action will build your package and push it to PyPI.

The tag for your release needs to match the `VERSION` string at the top of your `pyproject.toml` file. You should bump this version any time you release a new version of your package.

## Attribution

Adapted from [python-lib cookiecutter template](https://github.com/simonw/python-lib).
