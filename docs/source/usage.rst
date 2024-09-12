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
     - int, (default=2). 
       The number of the modalities.
   * - resolution
     - float, (default=0.6). 
       The resolution parameter, ranging from 0 to 1, controls the granularity of the clusters. Specifically, it adjusts the size of the clusters:
       Higher resolution values lead to more and smaller clusters, encouraging the algorithm to find finer structures in the data.
       Lower resolution values result in fewer and larger clusters, merging more points into broader groups.
   * - precomputed
     - bool, (default=False). 
       TriTan uses SVD to enhance the speed of factorization. 
       When precomputed is set to False, TriTan will run the SVD factorization within the model.
       When precomputed is set to True, users can provide their own SVD factorization to save the time. 
   * - svd_mods
     - When precomputed is set to True, uses should use svd_mods to input their own svd factorization as the format of dictionary:
       ::
           >>> u_rna, s_rna, v_rna = randomized_svd(X_gene, n_components=300, random_state=0)
           >>> u_atac, s_atac, v_atac = randomized_svd(X_atac, n_components=300, random_state=0)
           >>> svd_mods = {'rna': [u_rna, v_rna], 'atac': [u_atac, v_atac]}
   * - n_component
     - dic, (default: {'rna': [20,50], 'atac': [20,50]}). 
       Specifies the number of components for SVD decomposition in the cell and feature spaces for each modality. The number of components can be adjusted based on the dataset and corresponding singular value scree plots. The parameter allows for user-defined SVD decomposition for each modality. 



