===============================
Python Perforce
===============================

Pure python perforce API

* Free software: MIT license
* Documentation: https://python-perforce.readthedocs.org.

Features
--------

* Pythonic api to Perforce
* Pure python, no compiled extension

Installation
------------

::

    pip install python-perforce

Usage
-----

    >>> import perforce
    >>> p4 = perforce.connect()
    >>> revisions = p4.ls('//depot/path/to/file.txt')
    >>> print(revisions)
    [<Revision 1: file.txt>]
    >>> p4.ls('//depot/path/....txt')
    [<Revision 1: file.txt>, <Revision 2: foo.txt>]
    >>> cl = p4.findChangelist('my description')
    >>> with cl:
    ...     cl.append(revisions[0])
    ...     p4.add('path/to/add.txt', cl)
    >>> cl.description
    'my description'
    >>> cl.description = 'something else'
    >>> cl.submit()
    >>> client = perforce.Client('my_client')
    >>> print(client.stream)
    //streams/main
    >>> print(client.root)
    Path(/path/to/root)
