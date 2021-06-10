############################################################################
#################### Dependency: batteryho/gpu-jupyter #####################
############################################################################

FROM batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04
LABEL maintainer="Batteryhob <gorokke18@gmail.com>"

############################################################################
#################### Dependency: tensorflow-notebook #######################
############################################################################

LABEL maintainer="Jupyter Project <jupyter@googlegroups.com>"

# Install Tensorflow
# RUN mamba install --quiet --yes \
#     'tensorflow=2.3.0' && \
#     mamba clean --all -f -y && \
#     fix-permissions "${CONDA_DIR}" && \
#     fix-permissions "/home/${NB_USER}"

RUN pip install --user --upgrade tensorflow==2.3.0