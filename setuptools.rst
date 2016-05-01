Setuptools
==========

Installation sur Debian::

    apt-get install python-setuptools


Distutils VS setuptools en pratique
-----------------------------------

Le fichier setup.py peut utiliser distutils ou setuptools...

distutils::

    from distutils.core import setup

setuptools::

    from setuptools import setup

Usage
-----

Help (seulement les commandes "communes")::

    python3 setup.py -h

Help (toutes les commandes)::

    python3 setup.py --help-commands

Commands::

    Standard commands:
      build             build everything needed to install
      build_py          "build" pure Python modules (copy to build directory)
      build_ext         build C/C++ extensions (compile/link to build directory)
      build_clib        build C/C++ libraries used by Python extensions
      build_scripts     "build" scripts (copy and fixup #! line)
      clean             clean up temporary files from 'build' command
      install           install everything from build directory
      install_lib       install all Python modules (extensions and pure Python)
      install_headers   install C/C++ header files
      install_scripts   install scripts (Python or otherwise)
      install_data      install data files
      sdist             create a source distribution (tarball, zip file, etc.)
      register          register the distribution with the Python package index
      bdist             create a built (binary) distribution
      bdist_dumb        create a "dumb" built distribution
      bdist_rpm         create an RPM distribution
      bdist_wininst     create an executable installer for MS Windows
      check             perform some checks on the package
      upload            upload binary package to PyPI

    Extra commands:
      bdist_egg         create an "egg" distribution
      develop           install package in 'development mode'
      egg_info          create a distribution's .egg-info directory
      test              run unit tests after in-place build
      setopt            set an option in setup.cfg or another config file
      upload_docs       Upload documentation to PyPI
      alias             define a shortcut to invoke one or more commands
      rotate            delete older distributions, keeping N newest files
      install_egg_info  Install an .egg-info directory for the package
      easy_install      Find/get/install Python packages
      saveopts          save supplied options to setup.cfg or other config file

Publier sur PyPI::

    python3 setup.py register
    python3 setup.py sdist upload

    ./setup.py register
    [...]
    We need to know who you are, so please choose either:
     1. use your existing login,
     2. register as a new user,
     3. have the server generate a new password for you (and email it to you), or
     4. quit
    Your selection [default 1]: 
    2
    Username: [...]
    Password: [...]
     Confirm: [...]
       EMail: [...]
    Registering [...] to https://pypi.python.org/pypi
    You will receive an email shortly.
    Follow the instructions in it to complete registration.

Mot de pass enregistré dans ~/.pypirc
