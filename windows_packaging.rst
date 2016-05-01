Windows Packaging
=================

Questions similaires
====================

- http://stackoverflow.com/questions/106725/how-to-bundle-a-python-application-including-dependencies
- http://stackoverflow.com/questions/2933/how-can-i-create-a-directly-executable-cross-platform-gui-app-using-python

Solutions
=========

Py2exe
------

- http://www.py2exe.org/

PyInstaller
-----------

- http://www.pyinstaller.org/
- https://github.com/pyinstaller/pyinstaller/releases

Sur le blog de Cyrille Rossant
------------------------------

- http://cyrille.rossant.net/create-a-standalone-windows-installer-for-your-python-application/

WinPython
---------

- https://winpython.github.io/

Mon idée
--------

Écrire un script install.bat qui:

- Vérifie si Python est installé : commandes "python" / "py" ok
- Vérifie la version de Python
- Vérifie qu'on peut bien appeler PIP
- Ping PyPi pour vérifier si le réseau est OK
- Lance la commande d'installation de PIP
- Copie des raccourcis de démarrage aux bon endroits
- Mets à jour les variables d'environnement (PATH, ...) si besoin
- Affiche un message d'erreur si une des étapes précédente a échouée

Assistants d'installation sur Windows
=====================================

https://en.wikipedia.org/wiki/List_of_installation_software

Windows Installer
-----------------

- https://en.wikipedia.org/wiki/Windows_Installer

NSIS
----

- https://en.wikipedia.org/wiki/Nullsoft_Scriptable_Install_System
- https://fr.wikipedia.org/wiki/Nullsoft_Scriptable_Install_System

Témoignages
===========

Sur https://linuxfr.org/news/la-genealogie-avec-gramps-3-4-1

::

    Ce qui est chiant sous windows, c'est l'effort démesuré pour packager
    l'application.
    
    Installation de l'environnement de dev : python, pywin, reportLab,
    pyopenssl, pil (…) pygtk-all-in-one (version 2.24.0 et non 2.24.1 buggée),
    sql alchemy (et tous les drivers de db qui vont bien).  Quelques modifs si
    les scripts sont pas portables (mal codés : genre des os.path.join
    oubliées, des locales à charger correctement…).  Empaqueter le tout avec
    pyinstaller : j'ai mis énormément de temps à mettre en place un fichier de
    spec potable qui me copie les dossiers etc, lib, share avec les bonnes dll
    pour avoir un thème Gtk post-windows98.  Si l'appli portable est stable
    (environ 30Mo), faire un installer avec Nsis.
    
    Aujourd'hui j'ai un script python qui me fait tout ça en quelques commandes
    mais ça m'a pris énormément de temps pour en arriver là. La doc est juste
    inexistante.

Numpy: https://github.com/numpy/numpy/tree/master/tools/win32build
