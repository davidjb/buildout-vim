Buildout and Vim
================

If you're looking to integrate Vim and Buildout for Python development, you've
come to the right place.  Read on to learn how to integrate these different
parts of Vim and add-ons.

YouCompleteMe
-------------

YCM is an autocompleter for Vim.  YCM talks to a backend server process and
uses the Jedi autocompletion library for Python to learn what you're typing and
try to complete it for you.  Because Buildout uses customised ``sys.path``
configuration in its scripts and environments, intergration becomes difficult
as the paths are a moving target.

The included ``vim.cfg`` Buildout configuration creates a suitable Python
interpreter for YCM's server process to use, such that it knows about suitable
Buildout packages.  You need to do a little work yourself though, and extend
``${python-vim:eggs}`` inside the configuration to ensure the interpreter is
aware of the eggs:

.. code:: ini

    [buildout]
    extends = https://github.com/davidjb/buildout-vim/raw/master/vim.cfg

    [python-vim]
    eggs +=
        ${omelette:eggs}
        ${instance:eggs}
        ${pyramid:eggs}
        ${whatever:eggs}

Beyond this, the config also generates a ``.vimrc`` file locally within the
Buildout directory.  With a suitable plugin for Vim, such as
https://github.com/MarcWeber/vim-addon-local-vimrc, this will automatically get
loaded, thus ensuring YCM's server process uses the given Buildout-generated
interpreter.

Load a Python file inside the Buildout directory somewhere and start
autocompleting!
