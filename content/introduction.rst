Introduction
============

Documentation "officielle":

- PyPA: https://www.pypa.io/
- PyPUG: https://python-packaging-user-guide.readthedocs.org/

Documentation intéressante:

- https://python-packaging-user-guide.readthedocs.org/
- http://sametmax.com/creer-un-setup-py-et-mettre-sa-bibliotheque-python-en-ligne-sur-pypi/ (nov 2012)
- http://sametmax.com/travailler-sur-une-lib-externe-a-votre-projet-proprement-en-python/ (oct 2014)
    astuce très propre et très utile pour ne pas avoir a résinstaller à chaque
    modification un programme ou une bibliothèque qu'on est en train de développer!
- http://stackoverflow.com/questions/6344076/differences-between-distribute-distutils-setuptools-and-distutils2  (sept 2014)


Voc
---

- Distribution package: https://python-packaging-user-guide.readthedocs.org/en/latest/glossary.html#term-distribution-package
- Wheel: https://python-packaging-user-guide.readthedocs.org/en/latest/glossary.html#term-wheel
- Egg: https://python-packaging-user-guide.readthedocs.org/en/latest/glossary.html#term-egg
- Source Distribution (or “sdist”): https://python-packaging-user-guide.readthedocs.org/en/latest/glossary.html#term-source-distribution-or-sdist


Installer un paquet en local
----------------------------

Petit tour d'horizon des principaux outils disponibles:

- distutils: basique mais intégré à la lib standard
- setuptools: standard de fait, plus riche mais pas dans la bibliothèque standard

  - https://setuptools.pypa.io/en/latest/setuptools.html
  - fourni aussi easy_install

- distutils2: abandonné
- dsitribute: mergé dans setuptools
- bento: non standard, non mature


Installer un paquet depuis internet
-----------------------------------

PyPI (http://pypi.python.org) : le site web où sont entreposés les paquets.

Petit tour d'horizon des principaux outils disponibles:

- easy_install
- pip

  - cf. http://sametmax.com/votre-python-aime-les-pip/
  - "pip est un easy_install en plus court à taper, plus puissant, plus souple,
    plus mieux".
  - pip va plus loin qu’easy_install, et permet carrément de gérer toutes les
    dépendances de son projet.
  - A partir des versions 2.7.9 et et 3.4, pip est fournit automatiquement avec
    Python.

