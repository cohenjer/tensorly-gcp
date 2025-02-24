TensorLy-Gcp  
===============================================  
TensorLy-Gcp is a Python library for generalized parafac decomposition (GCP) [1] and its stochastic version (SGCP) [2] which allow using different kind of losses rather than only Euclidean  that builds on top of `TensorLy <http://tensorly.org/dev/installation.html>`_. Both algorithms aim at decreasing loss between the input tensor and estimated tensor by using gradient which is calculated according to the selected loss by the user.

While GCP implementation uses Limited-memory BFGS (LBFGS) method for optimization, SGCP uses ADAM optimization as in [2]. Following losses can be used in Tensorly-Gcp:

- Rayleigh
- Bernoulli odds
- Bernoulli logit
- Gamma
- Poisson count
- Poisson log
- Gaussian

Contributing
============
At the moment, only Numpy backend is supported to implement GCP and SGCP. This library can be compatible with other backends (Pytorch, Tensorflow, Jax, Mxnet) by improving LBFGS with the given information in `here <https://github.com/caglayantuna/tensorly-gcp/blob/master/tlgcp/utils/_lbfgs.py>`_. Then, this library can be merged in TensorLy.

Usage
============
It is possible select one of the losses from the list above according to your data distribution and you can apply generalized decomposition easily:

.. code:: python
    
    from tlgcp import generalized_parafac
    rank = 3
    loss = 'rayleigh'
    tensorgcp, errorsgcp = generalized_parafac(tensor, rank=rank, loss=loss)


Installing TensorLy-GCP  
=========================
Through pip
-----------

.. code:: 

   pip install tensorly-gcp   
   
From source
-----------

.. code::

  git clone https://github.com/tensorly/gcp
  cd gcp
  pip install -e .
  
  
  
References  
----------  
  
.. [1] Hong, D., Kolda, T. G., & Duersch, J. A. (2020). Generalized canonical polyadic tensor decomposition. SIAM Review, 62(1), 133-163. `Link <https://arxiv.org/abs/1808.07452>`_  
  
.. [2] Kolda, T. G., & Hong, D. (2020). Stochastic gradients for large-scale tensor decomposition. SIAM Journal on Mathematics of Data Science, 2(4), 1066-1095. `Link <https://arxiv.org/abs/1906.01687>`_
