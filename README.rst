treetagger-python
=================

A Python module for interfacing with the Treetagger by Helmut Schmid.

Copyright (C) 2018 Mirko Otto

For license information, see LICENSE.txt

Dependencies
------------

-  `TreeTagger <http://www.cis.uni-muenchen.de/~schmid/tools/TreeTagger/>`__
-  Python 3
-  `NLTK <http://nltk.org/>`__
-  treetagger.py is for Python 3

Tested with Treetagger 3.2, Python 3.6 and NLTK 3.3.0 on Ubuntu 18.04, OSX 10.13

Preparation
------------

The
`TreeTagger <http://www.cis.uni-muenchen.de/~schmid/tools/TreeTagger/>`__
is a copyrighted software by Helmut Schmid and
`IMS <http://www.ims.uni-stuttgart.de/>`__, please read the license
agreement before you download the TreeTagger package and language
models.

Before you can use the ``treetagger-python`` package please ensure you
have downloaded and installed the
`TreeTagger <http://www.cis.uni-muenchen.de/~schmid/tools/TreeTagger/>`__
itself.

After installing the ``TreeTagger`` program, please check if it works properly. 

The ``treetagger-python`` package now checks the installed language packs "language-utf8.par" in the ``lib`` directory. You can use the ``get_installed_lang`` function to show the languages. The corresponding executable files are used in the ``cmd`` directory under Linux and in the ``bat`` directory under Windows.

The English tagging examples and the Python doctest show the result with the "English parameter file (PENN tagset)" file.

Installation
-----------

Make sure that you know the HOME directory of the TreeTagger program.

To use the Python package ``treetagger-python``, you must either set the environment variable ``TREETAGGER_HOME`` or the path ``path_to_treetagger`` when the program is called. In section usage you can see the second option.

To set the environment variable ``TREETAGGER_HOME``, enter the path to the installation directory of ``TreeTagger``:

::

    export TREETAGGER_HOME='/path/to/your/TreeTagger/'


Clone the repository and change to this directory. In this directory the Python package ``treetagger-python`` can be used without installation.:

::

    clone https://github.com/miotto/treetagger-python.git
    cd treetagger-python

Usage
-----

Initialize by specifying the path ``path_to_treetagger``:

::

    from treetagger import TreeTagger
    tt = TreeTagger(path_to_treetagger='/path/to/your/TreeTagger/')

Show the installed languages:

::

    from treetagger import TreeTagger
    tt = TreeTagger(path_to_treetagger='/path/to/your/TreeTagger/')
    tt.get_installed_lang()

The output could look like this

::

    ['english', 'german']

Tagging a sentence from Python:

::

    from treetagger import TreeTagger
    tt = TreeTagger(path_to_treetagger='/path/to/your/TreeTagger/')
    tt.tag('What is the airspeed of an unladen swallow?')


The output is a list of [token, tag, lemma]:

::

    [['What', 'WP', 'what'], 
    ['is', 'VBZ', 'be'], 
    ['the', 'DT', 'the'], 
    ['airspeed', 'NN', 'airspeed'], 
    ['of', 'IN', 'of'], 
    ['an', 'DT', 'an'], 
    ['unladen', 'JJ', '<unknown>'], 
    ['swallow', 'NN', 'swallow'], 
    ['?', 'SENT', '?']]

Tagging a german sentence from Python:

::

    from treetagger import TreeTagger
    tt = TreeTagger(path_to_treetagger='/path/to/your/TreeTagger/', language='german')
    tt.tag('Das Haus hat einen großen hübschen Garten.')

The output is a list of [token, tag, lemma]:

::

    [['Das', 'ART', 'die'], 
    ['Haus', 'NN', 'Haus'], 
    ['hat', 'VAFIN', 'haben'], 
    ['einen', 'ART', 'eine'], 
    ['großen', 'ADJA', 'groß'], 
    ['hübschen', 'ADJA', 'hübsch'], 
    ['Garten', 'NN', 'Garten'], 
    ['.', '$.', '.']]
