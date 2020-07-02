# cookiecutter-mf-bp
- python cookiecutter template supporting Makefile and Best Practices(black,flake8) 

## rookie attempt at combination of two projects   
- alexkey/cookiecutter-lux-python
- sourcery-ai/python-best-practices-cookiecutter

Current state is Iffy...some of the make works...git hooks?
- First commit.

Cookiecutter template for a Python package.
The boilerplate Python project that aims to create facility for maintaining of the package easily. It considering tools for building, testing and distribution.

Get Started
This template provides a basic structure for an idiomatic Python package with a convenient Makefile-facility and additional helpers.
Template can be configured using Cookiecutter's CLI or by altering parameters directly in cookiecutter.json.
Requirements
There are a couple of tools for building, packaging, documentation and so on, that must be installed.
GNU sed (brew install gnu-sed for macOS),

- ripgrep (optionally),
- awk,
- Docker,Virtualenv,Sphinx (for sphinx-build and sphinx-apidoc).

To check availability of main tools just type make or make doc.
To get help about available Makefile targets type:  
- make help

Creating the virtual environment
- Compile Pip requirements from requirements.in to requirements.txt using pip-tools (via Docker):
- make requirements
Create the new virtual environment based on requirements.txt and requirements-test.txt:

```make venv
```
Install the package into a virtual environment in so-called "development mode":

- source .venv/bin/activate
- make install

### ...hard working here...

``` 
make uninstall
deactivate
Testing the package
Pytest is used as a test tool by default.
```

To run tests type (within a virtual environment):
```
make check
```
Building the package from scratch
Create a source distribution (tarball with sources):
```
make sdist
ls -al dist/*.tar.gz
```
Create a binary (wheel) distribution:
```
make dist
ls -al dist/*.whl
```
Dealing with containers
Display system-wide information:
```
make docker-info
```
Show all images, containers and volumes:
```
make docker-stats
```
Build the image according to Dockerfile:
```
make docker-build
```
Run temporary container in an interactive mode:
```
make docker-run
```
Remove all unused images, built containers and volumes:
```
make docker-clean
```
Documenting the project using Sphinx
Build an API documentation:
```
make apidoc
```
Build the documentation as a standalone HTML files:
```
make html
```
open doc/_build/html/index.html
GNU-style cleaners
Clean the project's directory (precompiled and temporary files):
```
make clean
```
Clean the project's build output (eggs, distributions, builds):
```
make distclean
```
Delete almost everything (including virtual environment):
```
make mostlyclean
```

## Best Practices
Best practices cookiecutter template as described in this blogpost.

### Features
- Testing with pytest
- Formatting with black
- Import sorting with isort
- Static typing with mypy
- Linting with flake8
- Git hooks that run all the above with pre-commit
- Deployment ready with Docker
- Continuous Integration with GitHub Actions

### Quickstart
#### Install pipx if pipenv and cookiecutter are not installed
python3 -m pip install pipx
python3 -m pipx ensurepath

#### Install pipenv using pipx
pipx install pipenv

#### Use cookiecutter to create project from this template
pipx run cookiecutter gh:sourcery-ai/python-best-practices-cookiecutter

#### Enter project directory
cd <repo_name>

#### Initialise git repo
git init

#### Install dependencies
pipenv install --dev

#### Setup pre-commit and pre-push hooks
pipenv run pre-commit install -t pre-commit
pipenv run pre-commit install -t pre-push
