.. include:: install-warning.rst

* Which version of MXNet does AutoGluon support?

   Currently, AutoGluon supports MXNet>=1.7.0. In order to ensure that you are installing mxnet
   larger than 1.7.0, you can use

   .. code-block::

     # For CPU
     python3 -m pip install "mxnet<2.0.0, >=1.7.0"

     # For GPU users, CUDA 101
     python3 -m pip install "mxnet_cu101<2.0.0, >=1.7.0"

* I cannot install the package and it reports the error "XXX is not a supported wheel on this platform".

   One possibility is that you are using an older version of pip. Try to upgrade your pip to a version later than "19.0.0", e.g., use the following command:

   .. code-block::

     python3 -m pip install --upgrade pip --user
     python3 -m pip install --upgrade setuptools --user

* I see the error "ERROR: No matching distribution found for mxnet<2.0.0,>=1.7.0b20200713".

   It might be due to the out-dated pip version. Try to upgrade the pip via:

   .. code-block::

     python3 -m pip install --upgrade pip --user
     python3 -m pip install --upgrade setuptools --user

* How can I install the customized mxnet (incubating) on SageMaker Notebook?

   You should choose the **conda_python3** kernel and then install the MXNet via

   .. code-block::

     # For CPU users
     python3 -m pip install "mxnet<2.0.0"

     # For GPU users, CUDA 101
     python3 -m pip install "mxnet_cu101<2.0.0"

* While running AutoGluon, I get error message "Check failed: e == cudaSuccess: CUDA: initialization error".

  You may have the wrong version of MXNet installed for your CUDA version.
  Match the CUDA version carefully when following the installation instructions (`nvcc --version`).

* On MacOS I am getting a segmentation fault when trying to train LightGBM / XGBoost.

   You need to install libOMP 11 to avoid segmentation faults on MacOS when training LightGBM / XGBoost:

   .. code-block::

      # brew install wget
      wget https://raw.githubusercontent.com/Homebrew/homebrew-core/fb8323f2b170bd4ae97e1bac9bf3e2983af3fdb0/Formula/libomp.rb
      brew uninstall libomp
      brew install libomp.rb
      rm libomp.rb

   For more information, refer to https://github.com/microsoft/LightGBM/issues/4897

* Does AutoGluon support ARM/M1 Mac?
  
  AutoGluon does not officially support ARM/M1 Mac. For more information, refer to https://github.com/awslabs/autogluon/issues/1242
