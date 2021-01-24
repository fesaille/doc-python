# Python development environment

## python version management

### Pyenv

### Conda

## Packaging

### Pip

Pip <badge-stars repo='pypa/pip'></badge-stars> <badge-doc
href="https://pip.pypa.io/en/stable"></badge-doc> is the package installer for
Python.

### Wheel

This library <badge-stars repo='pypa/wheel'></badge-stars> <badge-doc
href="https://wheel.readthedocs.io/"></badge-doc> <badge-pep
nr='427'></badge-pep> <badge-pep nr='425'></badge-pep> is the reference
implementation of the Python wheel packaging standard, as defined in PEP 427. It
has two different roles:

- A setuptools extension for building wheels that provides the bdist_wheel
  setuptools command
- A command line tool for working with wheel files

### PyOxyder

PyOwyder <badge-stars repo='indygreg/PyOxidizer'></badge-stars> <badge-doc
href='https://pyoxidizer.readthedocs.io'></badge-doc> is a utility for producing
binaries that embed Python.

It can be used in case of virtualenv with symlink to the python interpreter
(e.g. in the case of pipx)

### PyInstaller

PyInstaller <badge-stars repo='pyinstaller/pyinstaller'></badge-stars>
<badge-doc href='https://pyoxidizer.readthedocs.io'></badge-doc> bundles a
Python application and all its dependencies into a single package.

## `pyproject.toml`

This file, topic of <badge-pep nr='518'></badge-pep> lists the minimal
dependencies of the build system of a project in a declarative fashion.

<badge-pep nr='517'></badge-pep> add precisions on the build system interface,
by default `setuptools` <badge-doc
href='https://pip.pypa.io/en/stable/reference/pip/#build-system-interface'></badge-doc>.
In this case, and if `setup.py` is missing <badge-doc
href='https://setuptools.readthedocs.io/en/latest/setuptools.html#setup-cfg-only-projects'></badge-doc>,
setuptools emulates a dummy `setup.py` file containing only a
`setuptools.setup()` call.


??? Cite "About PEP 0518"

    [distutils](https://docs.python.org/3/library/distutils.html#module-distutils)
    When Python first developed its tooling for building distributions of
    software for projects, was the chosen solution. As time went on,
    [setuptools](https://pypi.python.org/pypi/setuptools) gained popularity to
    add some features on top of distutils. Both used the concept of a setup.py
    file.

### Tables

#### `build-system`

`[build-system]` table is used to store build-related data. Initially only one
key of the table will be valid and is mandatory for the table: `requires`.


A *build frontend* is a tool that users might run that takes arbitrary source
trees or source distributions and builds wheels from them. The actual building
is done by each source tree's *build backend*. In a command like pip wheel
some-directory/, pip is acting as a build frontend.

??? Example


    Usage with `setuptools` ```toml [build-system] # Minimum requirements for
    the build system to execute. requires = ["setuptools", "wheel"]  # PEP 508
    specifications. # This key is not mandatory as setuptools is default
    build-backend = "setuptools.build_meta" ```

    Usage with `poetry` ```toml [build-system] requires = ["poetry_core>=1.0.0"]
    build-backend = "poetry.core.masonry.api" ```

Tools should not require the existence of the `[build-system]` table. A
`pyproject.toml` file may be used to store configuration details other than
build-related data and thus lack a `[build-system]` table legitimately.

**Build backend interface**

In case a custom build backend interface is specified, [mandatory
hooks](https://www.python.org/dev/peps/pep-0517/#mandatory-hooks) -
`build_wheel` and `build_sdist` - must be specified. [Optional
hooks](https://www.python.org/dev/peps/pep-0517/#optional-hooks)

#### `tool`

The `[tool]` table is where any tool related to your Python project, not just
build tools, can have users specify configuration data as long as they use a
sub-table within `[tool]`, e.g. the flit tool would store its configuration in
`[tool.flit]`.

 Packaging

<badge-doc href='https://packaging.python.org/overview/' logo='python'>
</badge-doc>


[Blog post](https://snarky.ca/what-the-heck-is-pyproject-toml/)

## distutils

## Setuptools

`Setuptools` <badge-stars repo='pypa/setuptools'></badge-stars> <badge-doc
href='https://setuptools.readthedocs.io/en/latest/'></badge-doc> is a collection
of enhancements to the Python `distutils`.

## Virtual environements

### Pipenv

<badge-stars repo='pypa/pipenv'></badge-stars> <badge-doc href="https://pipenv-fork.readthedocs.io"></badge-doc>

[editable-dependencies](https://pipenv-fork.readthedocs.io/en/latest/basics.html#editable-dependencies-e-g-e)

```bash
pipenv install --dev -e .
```

### Poetry

<badge-stars repo='python-poetry/poetry'></badge-stars> <badge-doc href="https://python-poetry.org/docs/"></badge-doc> is a tool for dependency management and packaging.

**basic usage** <badge-doc href='https://python-poetry.org/docs/basic-usage/'></badge-doc> :

!!! Example

    ```bash
    # Create a new project
    poetry new <PROJECT_NAME>

    # Or init from an existing project
    poetry init

    # Add dependencies
    poetry add <DEP>

    # Install the dependencies
    poetry install

    # Run a command inside the env
    poetry run <COMMAND> <PARAMETERS>
    ```

!!! Important ""

    If already in a virtualenv, poetry will reuse it and will not create a new
    env. Linked environments can be displayed with `poetry env list`.


**Shell completion (zsh)**

```bash
poetry completions zsh > ~/.zsh/completion/_poetry
```

## Application manager

### Pipx

**pipx** <badge-stars repo='pipxproject/pipx'></badge-stars> <badge-doc href="https://pipxproject.github.io/pipx"></badge-doc> installs and run python applications in isolated environments.
