..
    Parts of the documentation is autogerated using kmdo, e.g. the usage

======
 ymlf
======

Command-line tool that parses **YAML** from ``stdin`` and writes the parsed
**YAML**, or a subset thereof, to ``stdout``.

Install
=======

Install ``ymlf`` system-wide via the pip:

.. code:: bash

  sudo pip install ymlf

Or install it at user-level via the pip:

.. code:: bash

  pip install ymlf --user

.. note::

  When doing user-level install, then include the ``pip`` binary install path
  in your ``PATH`` definition. For example ``PATH="$PATH:$HOME/.local/bin"``

Usage
=====

Pipe a **YAML** file to ``ymlf`` and it will echo it back without comments,
e.g.:

.. literalinclude:: ymlf-parse.cmd
   :language: bash

Yields:

.. literalinclude:: ymlf-parse.out
   :language: yaml

Pipe a **YAML** file to ``ymlf`` and provide an attribute filter, and it will
echo only a subset of the parsed **YAML** back, e.g.:

.. literalinclude:: ymlf-subset.cmd
   :language: bash

Yields:

.. literalinclude:: ymlf-subset.out
   :language: yaml

So, if you are looking for that one specific attribute, e.g.
``dev_geo.npugrp``, then you can filter it by invoking:

.. literalinclude:: ymlf-scalar.cmd
   :language: bash

Yielding:

.. literalinclude:: ymlf-scalar.out
   :language: yaml

Error Handling
--------------

When **YAML** is parsed and filtered successfully then ``ymlf`` has exit code
0. On error, exit-code is non-zero and a **YAML** comment is output. For
example, when attempting to get non-existing attribute ``dev_geo.foo``:

.. literalinclude:: ymlf-error.uone.cmd
   :language: bash

Then exit code is 1, and the following will be written to ``stdout``:

.. literalinclude:: ymlf-error.uone.out
   :language: bash
