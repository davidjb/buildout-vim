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

[buildout]
extends = 
