---
title: New Release to PyPI
---

When you're ready to push out a new version of your module to PyPI, you have to run two commands:

    python setup.py sdist bdist_wheel
    twine upload dist/*

The sdist command builds a source distribution of your module and compresses it into the default format for that OS (.tar.gz for UNIX systems.).  The wheel project provides the bdist_wheel command to setuptools for creating a wheel of your module -- this is the built-package format for Python modules.  Finally, twine is a module for interacting with PyPI.
