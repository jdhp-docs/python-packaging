Environnements virtuels Python
==============================

    "la notion simple d’avoir des installations de Python isolées de l’OS, et
    séparées les unes des autres pour chaque projet" (sametmax.com)

- venv_ : livré à partir de Python 3.3 seulement
- virtualenv_ : pour ceux "qui veulent quelque chose qui marche partout, tout
  le temps et facilement" (recommandé par sametmax.com)
- pyenv ?
- buildout_ : puissant mais compliqué


Virtualenv
----------

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
____

Intégré à Python v3.3 et plus.

Installation sur Debian/Ubuntu/...::

 # aptitude install python3-venv

* Documentation officielle: https://docs.python.org/3/library/venv.html#module-venv
* http://askubuntu.com/questions/279959/how-to-create-a-virtualenv-with-python3-3-in-ubuntu (cf. la 2e réponse)

Créer un environnement virtuel::

    pyvenv <PATH>

où ``<PATH>`` est le chemin du répertoire où créer l'environnement virtuel.

Entrer dans l'environnement virtuel (Unix)::

    source <PATH>/bin/activate

Sortir de l'environnement virtuel::

    deactivate


pyenv
-----

WTF?!

    "si vous utilisez Python 3.3, virtualenv est déjà inclus !!! (mais le script se nomme désormais pyvenv)"
    "C’est juste que virtualenv est intégré à Python 3 sous la forme de la commande pyenv, donc pas besoin de l’installer."
    (http://sametmax.com/les-environnement-virtuels-python-virtualenv-et-virtualenvwrapper/)




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
    (http://stackoverflow.com/questions/29950300/what-is-the-relationship-between-virtualenv-and-pyenv)


Qui dit vrais ?

Venv
----

Référence:

- https://docs.python.org/3/library/venv.html

