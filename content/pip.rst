Pip
===

http://sametmax.com/votre-python-aime-les-pip/ (sept 2012)

Linux::

    pip install pyax12
    pip install --upgrade pyax12
    pip uninstall pyax12

Pour installer des `versions de pre-release`_ ou `versions de développement`_::

    pip install --pre  pyax12

(``--pre`` include pre-release and development versions, by default, pip only finds stable versions)

Windows::

    py -m pip install pyax12
    py -m pip install --upgrade pyax12
    py -m pip uninstall pyax12



Twine
-----

Jusqu'en decembre 2013, les communications avec PyPI n'étaient pas cryptées, le
mot de passe etait transmi en clair !
https://anthony-monthe.me/weblog/2015/08/23/never-use-python-setuppy-upload/

Twine était une alternative sécurisée https://github.com/pypa/twine.

Depuis le problème est corrigé http://bugs.python.org/issue12226

.. _versions de pre-release: https://www.python.org/dev/peps/pep-0440/#pre-releases
.. _versions de développement: https://www.python.org/dev/peps/pep-0440/#developmental-releases
