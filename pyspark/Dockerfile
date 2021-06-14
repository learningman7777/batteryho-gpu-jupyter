############################################################################
#################### Dependency: pyspark-notebook ##########################
############################################################################

FROM jupyter/pyspark-notebook:ubuntu-20.04
LABEL maintainer="Batteryhob <gorokke18@gmail.com>"

############################################################################
#################### Dependency: aws-sdk ###################################
############################################################################

USER root

# hadoop version: 3.2 (https://hub.docker.com/layers/jupyter/pyspark-notebook/ubuntu-20.04/images/sha256-f95e3818d78d2c096764a69887119cc793cf653d803d498d464693481cec787a?context=explore)
# aws-java-sdk version: 1.11.375 (https://mvnrepository.com/artifact/org.apache.hadoop/hadoop-aws/3.2.0)
# Install aws-sdk
RUN wget https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk/1.11.375/aws-java-sdk-1.11.375.jar -P $SPARK_HOME/jars/
RUN wget https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/3.2.0/hadoop-aws-3.2.0.jar -P $SPARK_HOME/jars/

USER ${NB_UID}