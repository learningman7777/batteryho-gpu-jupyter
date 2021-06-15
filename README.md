# 넥슨 머신러닝파트 GPU-Jupyter

## 버전
nvidia/cuda 컨테이너 버전

- nvidia/cuda:11.0.3-cudnn8-devel-ubuntu20.04

주요 프레임워크 버전

- ubuntu 20.04
- cuda 11.0.3
- cudnn 8
- Dockerfile 에서 python 3.8로 변경(tensorflow-2.4.0 대응)


## cuda 11.0, cudnn8 대응 딥러닝 프레임워크 version
텐서플로우 : tensorflow-2.4.0

[<u>tensorflow offical</u>](https://www.tensorflow.org/install/source#gpu)

파이토치 : 공식 설치 명령어(stable version, pip, cuda11)
```
pip3 install torch==1.8.1+cu111 torchvision==0.9.1+cu111 torchaudio==0.8.1 -f https://download.pytorch.org/whl/torch_stable.html
```

[<u>pytorch offical</u>](https://pytorch.org/get-started/locally/)

## 모든 Dockerfile은 jupyter/docker-stacks에서 새로 가져와 빌드합니다.

[<u>docker-stacks</u>](https://github.com/jupyter/docker-stacks)

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
docker build -t batteryho/gpu-jupyter:11.0.3-cudnn8-devel-ubuntu20.04-base .
```

dockerhub에 푸쉬한다.

``` shell
docker push batteryho/gpu-jupyter:11.0.3-cudnn8-devel-ubuntu20.04-base
```

## base + pyspark

pyspark 폴더로 들어가 Dockerfile을 열고,

base 이미지의 태그로 수정하고 빌드한다.

빌드 명령어 예시는 다음과 같다. 

반드시 마지막 태그에 `-pyspark` 를 추가한다.

``` shell
cd pyspark
docker build -t batteryho/gpu-jupyter:11.0.3-cudnn8-devel-ubuntu20.04-pyspark .
```
dockerhub에 푸쉬한다.

``` shell
docker push batteryho/gpu-jupyter:11.0.3-cudnn8-devel-ubuntu20.04-pyspark
```

### Spark libraries

aws에 접근할 수 있는 spark aws 라이브러리 설치한다.

hadoop-aws는 hadoop과 버전의 같아야 한다.

[The versions of hadoop-common and hadoop-aws must be identical.](https://hadoop.apache.org/docs/stable/hadoop-aws/tools/hadoop-aws/index.html#:~:text=The%20versions%20of%20hadoop-common%20and%20hadoop-aws%20must%20be,dependencies%20unique%20to%20it%2C%20the%20AWS%20SDK%20JAR.)

hadoop-aws는 aws-java-sdk-bundle에 dependency 버전을 찾아야 한다.
[The versions of hadoop-common and hadoop-aws must be identical.](https://mvnrepository.com/artifact/org.apache.hadoop/hadoop-aws/3.2.0)

``` Dockerfile
RUN wget https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk-bundle/1.11.375/aws-java-sdk-bundle-1.11.375.jar -P $SPARK_HOME/jars/
RUN wget https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/3.2.0/hadoop-aws-3.2.0.jar -P $SPARK_HOME/jars/
```

## base + tensorflow

tensorflow 폴더로 들어가 Dockerfile을 열고,

base 이미지의 태그로 수정하고 빌드한다.

빌드 명령어 예시는 다음과 같다. 

반드시 마지막 태그에 `-tensorflow` 를 추가한다.

``` shell
cd tensorflow
docker build -t batteryho/gpu-jupyter:11.0.3-cudnn8-devel-ubuntu20.04-tensorflow .
```
dockerhub에 푸쉬한다.

``` shell
docker push batteryho/gpu-jupyter:11.0.3-cudnn8-devel-ubuntu20.04-tensorflow
```

## base + pytorch

pytorch 폴더로 들어가 Dockerfile을 열고,

base 이미지의 태그로 수정하고 빌드한다.

빌드 명령어 예시는 다음과 같다. 

반드시 마지막 태그에 `-pytorch` 를 추가한다.

``` shell
cd pytorch
docker build -t batteryho/gpu-jupyter:11.0.3-cudnn8-devel-ubuntu20.04-pytorch .
```
dockerhub에 푸쉬한다.

``` shell
docker push batteryho/gpu-jupyter:11.0.3-cudnn8-devel-ubuntu20.04-pytorch
```