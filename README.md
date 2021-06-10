# 넥슨 머신러닝파트 GPU-Jupyter

## 모든 Dockerfile은 jupyter/docker-stacks에서 새로 가져옵니다.

https://github.com/jupyter/docker-stacks

## base 이미지 빌드

base 폴더로 들어가 Dockerfile을 열고, nvidia/cuda 이미지의 태그를 원하는 버전으로 수정한 뒤, 

빌드한다.

base 이미지의 레이어 빌드 순서는 다음과 같다.

- nvidia/cuda
- jupyter/base-image
- jupyter/minimal-notebook
- jupyter/scipy-notebook

jupyter-docker-stacks 에 따른다.

![주피터노트북레이어](https://jupyter-docker-stacks.readthedocs.io/en/latest/_images/inherit.svg)

빌드 명령어 예시는 다음과 같다. 반드시 선택한 nvidia/cuda 버전과 빌드 이미지의 태그를 일치시킨다.

``` shell
cd base
docker build -t batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04 .
```

dockerhub에 푸쉬한다.

``` shell
docker push batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04
```

## base + pyspark

pyspark 폴더로 들어가 Dockerfile을 열고,

base 이미지의 태그로 수정하고 빌드한다.

빌드 명령어 예시는 다음과 같다. 

반드시 마지막 태그에 `-pyspark` 를 추가한다.

``` shell
cd pyspark
docker build -t batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04-pyspark .
```
dockerhub에 푸쉬한다.

``` shell
docker push batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04-pyspark
```

## base + tensorflow

tensorflow 폴더로 들어가 Dockerfile을 열고,

base 이미지의 태그로 수정하고 빌드한다.

빌드 명령어 예시는 다음과 같다. 

반드시 마지막 태그에 `-tensorflow` 를 추가한다.

``` shell
cd tensorflow
docker build -t batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04-tensorflow .
```
dockerhub에 푸쉬한다.

``` shell
docker push batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04-tensorflow
```

## base + pytorch

pytorch 폴더로 들어가 Dockerfile을 열고,

base 이미지의 태그로 수정하고 빌드한다.

빌드 명령어 예시는 다음과 같다. 

반드시 마지막 태그에 `-pytorch` 를 추가한다.

``` shell
cd pytorch
docker build -t batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04-pytorch .
```
dockerhub에 푸쉬한다.

``` shell
docker push batteryho/gpu-jupyter:10.1-cudnn7-devel-ubuntu18.04-pytorch
```