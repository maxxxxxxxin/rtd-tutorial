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

.. list-table:: 
   :header-rows: 1

   * - Parameter
     - Description
   * - n_modality
     - The number of the modalities. [default: 2]
   * - resolution
     - The resolution for the cell model selection with a value range from 0 to 1. [default: 0.6]
   * - precomputed : bool, default=True
     - TriTan uses SVD to enhance the speed of factorization. When precomputed is set to False, TriTan will run the SVD factorization within the model. When precomputed is set to True, users can provide their own SVD factorization to save the time. [default: False]
   * - svd_mods
     - When precomputed is set to True, uses should use svd_mods to input their own svd factorization as the format of dictionary:
       ::
           >>> u_rna, s_rna, v_rna = randomized_svd(X_gene, n_components=300, random_state=0)
           >>> u_atac, s_atac, v_atac = randomized_svd(X_atac, n_components=300, random_state=0)
           >>> svd_mods = {'rna': [u_rna, v_rna], 'atac': [u_atac, v_atac]}
   * - n_component
     - Specifies the number of components for SVD decomposition in the cell and feature spaces for each modality. The number of components can be adjusted based on the dataset and corresponding singular value scree plots. The parameter allows for user-defined SVD decomposition for each modality. [default: {'rna': [20,50], 'atac': [20,50]}]



