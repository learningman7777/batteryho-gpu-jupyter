############################################################################
#################### Dependency: batteryho/gpu-jupyter #####################
############################################################################

FROM batteryho/gpu-jupyter:11.0.3-cudnn8-devel-ubuntu20.04-base
LABEL maintainer="Batteryhob <gorokke18@gmail.com>"

############################################################################
#################### Dependency: pytorch ###################################
############################################################################

# Upgrade pip
RUN pip install --upgrade pip

# Install pytorch
RUN pip install torch==1.8.1+cu111 torchvision==0.9.1+cu111 torchaudio==0.8.1 -f https://download.pytorch.org/whl/torch_stable.html

USER root
RUN apt update
RUN apt install git
RUN apt install openssh-server -y

USER jovyan

# Install libs
RUN pip install opencv-python \
    imageio \
    imageio-ffmpeg \
    pycocotools>=2.9.2
	
