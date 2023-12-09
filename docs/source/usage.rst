Usage
=====

.. _installation:

Installation
------------

To use Lumache, first install it using pip:

.. code-block:: console

    (.venv) $ pip install tritan

Basic usage
-----------

To use the intNMF class and other functions in the package add directory to your
python path i.e.

.. code-block:: python

    path_to_nmf = 'your-path-here'
    module_path = os.path.abspath(os.path.join(path_to_nmf))
    if module_path not in sys.path:
        sys.path.append(module_path)
    from nmf_models_mod_updates import intNMF, log_tf_idf

You can then initialise a joint NMF model:

.. code-block:: python

    nmf_model = intNMF(5)

The only required argument is the number of topics. The model can then be
trained using the .fit() method:

.. code-block:: python

    nmf_model.fit(rna_mat, atac_mat)

where both rna_mat and atac_mat are sparse matrices. It is recommended to use
muon and scanpy for single cell multiome analysis. The joint low dimensional
embedding can be added to a muon object as follows:

.. code-block:: python

    # write to joint embeding
    mudata.obsm['intNMF'] = nmf_model.theta
    # write joint embedding to one of the anndata objects
    mudata['rna'].obsm['intNMF'] = nmf_model.theta

The loadings can also be stored.

.. code-block:: python

    # write rna loadings
    mudata['rna'].varm['intNMF'] = nmf_model.phi_rna
    # write atac laodings
    mudata['atac'].varm['intNMF'] = nmf_model.phi_atac

See the :doc:`tutorials` section for jupyter notebooks with more details.
