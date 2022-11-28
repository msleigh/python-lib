# {{ cookiecutter.hyphenated }}

[![PyPI](https://img.shields.io/pypi/v/{{ cookiecutter.hyphenated }}.svg)](https://pypi.org/project/{{ cookiecutter.hyphenated }}/){% if cookiecutter.github_username %}
[![Tests](https://github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.hyphenated }}/actions/workflows/test.yml/badge.svg)](https://github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.hyphenated }}/actions/workflows/test.yml)
[![Changelog](https://img.shields.io/github/v/release/{{ cookiecutter.github_username }}/{{ cookiecutter.hyphenated }}?include_prereleases&label=changelog)](https://github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.hyphenated }}/releases)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://github.com/{{ cookiecutter.github_username }}/{{ cookiecutter.hyphenated }}/blob/main/LICENSE){% endif %}
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/python/black)

{{ cookiecutter.description }}

---

## Requirements

{{cookiecutter.lib_name }} requires Python 3.7+. It is tested on Linux and macOS.

## Installation

Install this library using `pip`:

```bash
pip install {{ cookiecutter.hyphenated }}
```

## Configuration

Configuration instructions go here.

## Usage

Usage instructions go here.

## Development

To contribute to this library, first checkout the code. Then create a new
virtual environment:

```bash
cd {{ cookiecutter.hyphenated }}
python -m venv .venv
source .venv/bin/activate
```

Now install the dependencies and test dependencies:

```bash
pip install -e '.[test]'
```

To run the tests:

```bash
pytest
```
