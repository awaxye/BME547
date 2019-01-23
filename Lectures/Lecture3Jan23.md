# Python virtual environments

## Setting Up Virtual Enironments
* Heavily recommended for local computer usage, 100% required for remote
  deployment.
* Python has a stadard library of functionality; additional functionality is
  imported into projects through additional packages.
  + PyPI is the most popular repository of Python packages.  Conda is an
    alternative repository.
  + `pip` is the tool to install packages from PyPI; `conda` for the Conda
    repositories.
  + Different projects will require different packages.  Installing just the
    packages that you need for each Python project:
    - Prevents package version conflicts between different projects.
    - Establishes a minimized storage footprint of packages for each project
      (though commonly-used packages in many projects will be replicated).

previously we used `virtualenv`  to create virtual environments for our Python project.
* Steps towards creating and configuring a virtual environment:
  1. `virtualenv env` (creates a local python virtual environment in `env/`)
  1. `source env/bin/activate` (activate the working environment)
  1. `pip install $PACKAGENAME`
  1. Collect all of the packages that you need in a `requirements.txt` file
     [optionally include versions], and install all at once: `pip install -r
     requirements.txt`.  This is very useful for replicating virtual
     environments on new systems (e.g., CI testing setups).
  1. Work
  1. `deactivate`

Several methods exist however.

## Let's create a virtual environment a different way

new repository mkdir test_venv, cd test_venv, git init

Now use venv to create virual environment
* works the same way as virtualenv env but doesn't copy all the python binaries
* can be easier, less complicated but newer approach (Python 3.3 or later)\


`python -m venv .venv`

`source .venv/Scrpits/activate`


lets take a look in .venv directory
can also deactivate
let's also look at what python we are using  

`which python`

## but what if I have a different setup?

Dr. Ward has put together a nice resource:

https://github.com/dward2/BME547/blob/master/Resources/virtual_environments.md

