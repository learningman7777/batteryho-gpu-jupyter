############################################################################
#################### Dependency: batteryho/gpu-jupyter #####################
############################################################################

FROM batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04
LABEL maintainer="Batteryhob <gorokke18@gmail.com>"

############################################################################
#################### Dependency: PyTorch ###################################
############################################################################

LABEL maintainer="Jupyter Project <jupyter@googlegroups.com>"

# Install PyTorch with dependencies
RUN conda install --quiet --yes \
    pyyaml mkl mkl-include setuptools cmake cffi typing

# Check compatibility here:
# https://pytorch.org/get-started/locally/
# Installation via conda leads to errors installing cudatoolkit=10.1
RUN pip install torch torchvision torchaudio torchviz