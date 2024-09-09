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
     - The number of the modalities [default: 2]
   * - resolution
     - The resolution for the cell model selection with a value range from 0 to 1 [default: 0.6]
   * - precomputed
     - TriTan uses SVD to enhance the speed of factorization. When precomputed is set to False, TriTan will run the SVD factorization within the model. When precomputed is set to True, users can provide their own SVD factorization based on prior knowledge. [default: False]
   * - n_component
     - Specifies the number of components for SVD decomposition in the cell and feature spaces when precomputed is set to False. The number of components can be adjusted based on the dataset and corresponding singular value scree plots. The parameter allows for user-defined SVD decomposition for each modality.
       ::
           >>> svd = [#feature(mod1), #cell(mod1), #feature(mod2), #cell(mod2)]
   * - svd_mod1 & svd_mod2
     - When precomputed = True, the user should input their precomputed SVD matrices, for example:
       ::
           >>> u_rna, s_rna, v_rna = randomized_svd(X_gene, n_components=300, random_state=0)
           >>> u_atac, s_atac, v_atac = randomized_svd(X_atac, n_components=300, random_state=0)
           >>> rna=[u_rna, v_rna]
           >>> atac=[u_atac, v_atac]
           >>> svd=[50, 300, 50, 300]
           >>> tritan = TriTan.TriTan(n_component=svd, precomputed=True, svd_mod1=rna, svd_mod2=atac)
   * - tfidf
     - TF-IDF transformation on input data
   * - alpha
     - When tfidf = False, users can input alpha to achieve scale balance across omics


