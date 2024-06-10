# Inverse design of dual-phase steel microstructures using generative machine learning model and Bayesian optimization
This is a part of my PhD reserach project on designing DP steel microstructures with target mechanical properties using Varational autoencoder ad generative model and Bayesian optimization as model for Invserse microstructure property relationship. 

The corresponding research paper has beed published in the International Journal of Plasticity and is available at the following link https://doi.org/10.1016/j.ijplas.2023.103776

The main workflow can can be found as below [Workflow](https://ars.els-cdn.com/content/image/1-s2.0-S0749641923002607-ga1_lrg.jpg)

Here we present an ML-based approach for the design of DP steel microstructures with specific properties. Our approach is based on a variational autoencoder (VAE) to automatically identify low-dimensional microstructure representations and Bayesian optimization (BOpt) to identify the combination of microstructure descriptors leading to the desired mechanical behavior. For a proof of concept study, we use multi-level Voronoi tessellation in order to speed up the generation of the diverse data set that is required to adequately explore the microstructure parameter space. These microstructures contain information about phase and orientation of each grain. While the use of synthetic microstructures means that the microstructures are simplified, our data contains quantitative features seen in measured DP steel microstructures and the use of an experimentally acquired data set would not change the workflow of the proposed approach. Fig. 1 shows the workflow of the proposed method which consists of the following steps:


1. **Creation of training data:** First, we create synthetic 2D polycrystalline DP steel microstructures with phase and crystal orientation distribution data by means of multi-level Voronoi tessellation.
2. **Training of a generative ML model**: Next, we train a generative ML model with the microstructure data set. The ML model consists of an encoder–decoder network which learns microstructural features in a low-dimensional space and is used to generate novel microstructures.
3. **Bayesian optimization:** Finally, we train a Gaussian process model as a surrogate for the microstructure–property relationship to enable optimization using the low-dimensional representation. The Gaussian process model is sequentially updated with samples suggested by BOpt and the corresponding mechanical property calculated from a full-field crystal plasticity model.

The methods used in this work 1.e, 1) to create DP steel microstructure dataset, 2) architectture of the VAE model and its training procedure, and 3) implementing Bayesian optimization algorithem can be found in the Journla paper.

We have implemented the proposed approach using open source software such as [Keras](https://keras.io/) and [Scikit-learn](https://scikit-learn.org/stable/) for Machine learning, [GPyOpt}(https://sheffieldml.github.io/GPyOpt/) for Bayesian optimization, and [DAMASK](https://damask.mpie.de/) for Crystal plasticity simulations.

Here we share the main code used in the research work. All the code is written in Python and is available in three Jupyter notebooks.

1. *Synthetic Microstructure Generation and DAMASK Simulation.ipynb* explains the basic procedure to create a synthetic dual-phase steel microstructure using the Voronoi tessellation method available from the DAMASK software.
2. *VAE_LatentDim_256.ipynb* explains the main architecture and the training procedure for the VAE model.
3. *BayesianOptimization_16D.ipynb* explains the code to perform Bayesian optimization using the microstructure latent space variables identified by the VAE model.

The trained parts of the VAE model can be found under *VAE256_500Epochs_encoder.hdf5* and *VAE256_500Epochs_decoder.hdf5*, and the necessary configuration files to run the DAMASK simulations can be found in the *config* folder.
