Environnements virtuels Python
==============================

UPDATE: à lire:

- http://masnun.com/2016/04/10/python-pyenv-pyvenv-virtualenv-whats-the-difference.html
- https://realpython.com/blog/python/python-virtual-environments-a-primer/
- http://pewetheb.blogspot.fr/2015/11/virtual-environment-in-python.html    (ok)
- venv https://www.python.org/dev/peps/pep-0405/
- venv https://docs.python.org/3/library/venv.html
- virtualenv https://virtualenv.pypa.io/en/stable/
- virtualenv et virtualenvwrapper http://sametmax.com/les-environnement-virtuels-python-virtualenv-et-virtualenvwrapper/ (oct 2012)
- http://homework.nwsnet.de/releases/8aff/


    "la notion simple d’avoir des installations de Python isolées de l’OS, et
    séparées les unes des autres pour chaque projet" (sametmax.com)

Pour résumer, ancien outil tiers (toujours très utilisé ?) pour virtualliser les paquets python:

- virtualenv_ : outil externe populaire qui était là bien avant venv. à l'avantage de fonctionner avec de vielles versions de Python (<3.3)
- virtualenvwrapper: basically, this is a script to wrap virtualenv so that it is easier for us to work on multiple virtual environments.

La nouvelle alternative officielle à virtualenv pour virtualliser les paquets python:

- venv_ : une librairie intégrée à Python depuis Python 3.3 pour faire la même chose que virtualenv mais intégré de base dans python (c'est le seul outil "officiel" de la liste). It looks pretty much similar to virtualenv but "venv has less features compared to virtualenv".
- pyvenv_ (à ne pas confondre avec pyenv): un script de venv_ (déprécié depuis Python 3.6 au profit de `python3 -m venv`)

Outil tiers (scripts shell) pour installer plusieurs interprètes Python:

- pyenv (à ne pas confondre avec pyvenv) : outil tiers (scripts shell) pour installer plusieurs *interprètes* Python sur un même système (par ex. CPython 2.6, CPython 3.4, Pypy, IronPyhon, ...). Rien à voir avec les outils précédents mais son nom entretient une certaine confusion avec venv et pyvenv
- Pythonbrew: ancien nom de pyenv (?)

Misc:

- buildout_ : puissant mais compliqué


Virtualenv
----------

Virtualenv est un outil **tiers** développé par Ian Bicking qui permet d'isoler des site packages

- https://www.python.org/dev/peps/pep-0405/#id4
- https://virtualenv.pypa.io/en/stable/

Tout est très bien expliqué dans le tutoriel suivant:

- http://sametmax.com/les-environnement-virtuels-python-virtualenv-et-virtualenvwrapper/ (oct 2012)

Pour résumer, principales commandes:

Créer un environnement virtuel::

    virtualenv <PATH>

où ``<PATH>`` est le chemin du répertoire où créer l'environnement virtuel.

Créer un environnement virtuel pour une version spécifique de python (par ex
python 3.4)::

    virtualenv -p /usr/bin/python3.4 <PATH>

Créer un environnement virtuel vierge (ie qui n’hérite pas des libs du système
et a seulement accès aux libs standards de Python)::

    virtualenv --no-site-packages <PATH>

Pour desactiver setuptools et pip::

     --no-setuptools --no-pip

Entrer dans l'environnement virtuel (Unix)::

    source <PATH>/bin/activate

Entrer dans l'environnement virtuel (Windows)::

    <PATH>\Scripts\activate.bat

Sortir de l'environnement virtuel::

    deactivate


Virtualenvwrapper
-----------------

Pour passer facilement d'un environnement virtuel à l'autre.

Cf:

- http://sametmax.com/les-environnement-virtuels-python-virtualenv-et-virtualenvwrapper/ (oct 2012)


venv
----

- https://docs.python.org/3/library/venv.html#venv-def
- La PEP qui défini venv: https://www.python.org/dev/peps/pep-0405/

Definition (https://www.python.org/dev/peps/pep-0405/#abstract):

    This PEP proposes to add to Python a mechanism for lightweight "virtual
    environments" with their own site directories, optionally isolated from
    system site directories. Each virtual environment has its own Python binary
    (allowing creation of environments with various Python versions) and can
    have its own independent set of installed Python packages in its site
    directories, **but shares the standard library with the base installed
    Python**. 

Motivations: https://www.python.org/dev/peps/pep-0405/#motivation

    "To use venv, the workflow is quite similar to virtualenv. First, you create the virtual environment directory. Next, activate the virtual environment."

    http://pewetheb.blogspot.fr/2015/11/virtual-environment-in-python.html

Intégré à Python v3.3 et plus.

Installation sur Debian/Ubuntu/... (il est officiellement "intégré" à Python3 mais Debian a éclaté Python3 en plusieurs paquets)::

 # aptitude install python3-venv

* Documentation officielle: https://docs.python.org/3/library/venv.html
* http://askubuntu.com/questions/279959/how-to-create-a-virtualenv-with-python3-3-in-ubuntu (cf. la 2e réponse)

Sur Debian/Ubuntu, il y a un "bug" (en réalité c'est un choix des dev Debian
TODO...): par défaut, les sitepackages ne sont pas accessibles depuis
l'environnement virtuel Python (par exemple ``import numpy`` échoue même si
numpy est installé sur le système...).
Pour résoudre ce problème, il suffit de déclarer la variable d'environnement
``PYTHONPATH`` comme suit à la fin du fichier ``~/.bashrc``::

 export PYTHONPATH=${PYTHONPATH}:/usr/lib/python3/dist-packages

et de recharger le .bashrc en rouvrant le terminal ou en tapant::

 source ~/.bashrc

Pour plus de détails, cf. http://stackoverflow.com/questions/19210964/how-to-get-virtualenv-to-use-dist-packages-on-ubuntu.

Créer un environnement virtuel avec Python 3.3 à 3.5::

    pyvenv <PATH>

Créer un environnement virtuel avec Python 3.6 et +::

    python3 -m venv <PATH>

où ``<PATH>`` est le chemin du répertoire où créer l'environnement virtuel.

Entrer dans l'environnement virtuel (Unix)::

    source <PATH>/bin/activate

Sortir de l'environnement virtuel::

    deactivate


Pyenv
-----

https://github.com/yyuu/pyenv

pyenv does...

- Let you change the global Python version on a per-user basis.
- Provide support for per-project Python versions.
- Allow you to override the Python version with an environment variable.
- Search commands from multiple versions of Python at a time. This may be helpful to test across Python versions with tox.

In contrast with pythonbrew and pythonz, pyenv does not...

- Depend on Python itself. pyenv was made from pure shell scripts. There is no bootstrap problem of Python.
- Need to be loaded into your shell. Instead, pyenv's shim approach works by adding a directory to your $PATH.
- Manage virtualenv. Of course, you can create virtualenv yourself, or pyenv-virtualenv to automate the process.

*Pyenv* n'a rien à voir avec *virtualenv* et *pyvenv*.

    "*Pyenv* allows you to easily install multiple copies and multiple flavors of the
    Python interpreter. So you can not only install different versions of
    CPython, you can also install PyPy, Jython, Stackless Python and their
    different versions.
    [...]

    *pyvenv* and *virtualenv* allow you to create virtual environments so we can
    isolate our project dependencies. Why are they helpful? Say for example,
    you have one project which uses Django 1.6 still while your newer projects
    start with 1.9. When you install one version of Django, it replaces the
    other one, right? Virtual environments can rescue us from such situation."

    http://masnun.com/2016/04/10/python-pyenv-pyvenv-virtualenv-whats-the-difference.html

    "Pyenv and virtualenv are very different tools that work in different ways
    to do different things:

    Pyenv is a bash extension - will not work on Windows - that intercepts your
    calls to python, pip, etc., to direct them to one of several of the system
    python tool-chains. So you always have all the libraries that you have
    installed in the selected python version available - as such it is good for
    users who have to switch between different versions of python.

    VirtualEnv, is pure python so works everywhere, it makes a copy of,
    optionally as specific version of, python and pip local to the activate
    environment which may or may not include links to the current system
    tool-chain, if it does not you can install just a known subset of libraries
    into that environment. As such it is almost certainly much better for
    testing and deployment as you know exactly which libraries, at which
    versions, are used and a global change will not impact your module."
    
    http://stackoverflow.com/questions/29950300/what-is-the-relationship-between-virtualenv-and-pyenv


Un tutoriel pour pyenv: https://amaral.northwestern.edu/resources/guides/pyenv-tutorial

Virtual environments with Conda
-------------------------------

TODO...

See: http://conda.pydata.org/docs/using/envs.html

.. code-block:: bash

    conda create -n cta python=3.5 astropy matplotlib scipy scikit-learn numba cython

Next, switch to this new virtual environment and install some other useful tools for development:

.. code-block:: bash

     source activate cta

