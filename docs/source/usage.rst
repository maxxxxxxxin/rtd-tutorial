Usage
=====

.. _installation:

Installation
------------

To use TriTan, first install it using pip:

.. code-block:: console

    (.venv) $ pip install TriTan

Basic usages
-----------

Import TriTan as:

.. code-block:: python

   import TriTan

Initialise a TriTan model:

.. code-block:: python

    tritan = TriTan.TriTan()

The input to TriTan is a MuData object.
Train the model:

.. code-block:: python

    tritan.fit(mdata)
