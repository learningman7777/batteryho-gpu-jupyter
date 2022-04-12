FROM public.ecr.aws/j1r0q0g6/notebooks/notebook-servers/jupyter-tensorflow-cuda:master-e9324d39

# Upgrade pip
RUN pip install --upgrade pip

# install apt
USER root
RUN apt update
RUN apt install git
RUN apt install openssh-server -y

USER jovyan

# Install pytorch
RUN pip install torch==1.8.1+cu111 torchvision==0.9.1+cu111 torchaudio==0.8.1 -f https://download.pytorch.org/whl/torch_stable.html


# install - requirements.txt
COPY --chown=jovyan:users requirements.txt /tmp/requirements.txt
RUN python3 -m pip install -r /tmp/requirements.txt --quiet --no-cache-dir \
 && rm -f /tmp/requirements.txt

# Install libs
RUN pip install opencv-python \
    imageio \
    imageio-ffmpeg \
    pycocotools>=2.9.2
	
