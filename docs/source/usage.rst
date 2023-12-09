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

Parameters
-----------

.. code-block:: python

    tritan = TriTan.TriTan( n_modalities = 2, resolution = 10, epoch =30, resolution = 0.6, precomputed = False, svd_mod1= None, svd_mod2 = None, sparse = False, n_component= [20,50,20,50])

---------------------------------------------------------------------------------------------------------------------------------------------

n_modality ： the number of the modalities 

-----------

res_size : the resolution for the cell model selection with a value range from 0 to 1

epoch : iteration times [must larger than 20]

n_component ：when precomputed = False, you can define the number of the svd components as:

>>> svd = [#feature(mod1), #cell(mod1), #feature(mod2), #cell(mod2)]

svd_mod1 & svd_mod2 : when precomputed = True, the uses should input their precomputed svd matirces, for example:

>>> u_rna, s_rna, v_rna = randomized_svd(X_gene,n_components=300, random_state=0)   
>>> u_atac, s_atac, v_atac = randomized_svd(X_atac,n_components=300, random_state=0)
>>> rna=[u_rna,v_rna]
>>> atac=[u_atac,v_atac]
>>> svd=[50,300,50,300]
>>> tritan = TriTan.TriTan(n_component = svd , precomputed = True, svd_mod1 = rna, svd_mod2 = atac)



