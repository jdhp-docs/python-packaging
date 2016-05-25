Distutils
=========

- https://wiki.python.org/moin/Distutils/Tutorial
- https://docs.python.org/3/library/distutils.html
- https://wiki.python.org/moin/Distutils/

Fichiers à la racine du projet:

- MANIFEST.in
- setup.py

Voir https://wiki.python.org/moin/Distutils/Tutorial

::

    top
    |-- package
    |   |-- __init__.py
    |   |-- module.py
    |   `-- things
    |       |-- cross.png
    |       |-- fplogo.png
    |       `-- tick.png
    |-- runner
    |-- MANIFEST.in
    |-- README
    `-- setup.py 

MANIFEST.in
-----------

Ce fichier contient la liste des fichiers qui ne font pas partie du "paquet
python" mais qu'on souhaite ajouter au "paquet" (typiquement fichiers de
données tels que la documentation, les images, les fichiers json, les fichiers
de configuration, etc.)...


setup.py
--------

...


Usage
-----

Help (seulement les commandes "communes")::

    python3 setup.py -h

Help (toutes les commandes)::

    python3 setup.py --help-commands

Commands::

    Standard commands:
      build            build everything needed to install
      build_py         "build" pure Python modules (copy to build directory)
      build_ext        build C/C++ extensions (compile/link to build directory)
      build_clib       build C/C++ libraries used by Python extensions
      build_scripts    "build" scripts (copy and fixup #! line)
      clean            clean up temporary files from 'build' command
      install          install everything from build directory
      install_lib      install all Python modules (extensions and pure Python)
      install_headers  install C/C++ header files
      install_scripts  install scripts (Python or otherwise)
      install_data     install data files
      sdist            create a source distribution (tarball, zip file, etc.)
      register         register the distribution with the Python package index
      bdist            create a built (binary) distribution
      bdist_dumb       create a "dumb" built distribution
      bdist_rpm        create an RPM distribution
      bdist_wininst    create an executable installer for MS Windows
      check            perform some checks on the package
      upload           upload binary package to PyPI

Install::

    python3 setup.py install


Make a source distribution file (sdist != bdist)::

    python3 setup.py sdist


Uninstall:

    "Notably, `distutils does not have an uninstall command`_ at this time."
    (http://stackoverflow.com/questions/402359/how-do-you-uninstall-a-python-package-that-was-installed-using-distutils)

Register to PyPI::

    python3 setup.py register

Submitting to PyPI::

    python3 setup.py sdist upload

Clean up temporary files from 'build' command::

    python3 setup.py clean

Create a built (binary) distribution::

    bdist            

Create a "dumb" built distribution::

    bdist_dumb

Create an RPM distribution::

    bdist_rpm

Create an executable installer for MS Windows::

    bdist_wininst

.. _distutils does not have an uninstall command: http://bugs.python.org/issue4673
