FROM  phusion/baseimage:0.9.17

MAINTAINER  Author Name <author@email.com>

RUN echo "deb http://archive.ubuntu.com/ubuntu trusty main universe" > /etc/apt/sources.list

RUN apt-get -y update

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y -q python-software-properties software-properties-common

ENV JAVA_VER 8
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

RUN echo 'deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main' >> /etc/apt/sources.list && \
    echo 'deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main' >> /etc/apt/sources.list && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C2518248EEA14886 && \
    apt-get update && \
    echo oracle-java${JAVA_VER}-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections && \
    apt-get install -y --force-yes --no-install-recommends oracle-java${JAVA_VER}-installer oracle-java${JAVA_VER}-set-default && \
    apt-get clean && \
    rm -rf /var/cache/oracle-jdk${JAVA_VER}-installer

RUN update-java-alternatives -s java-8-oracle

RUN echo "export JAVA_HOME=/usr/lib/jvm/java-8-oracle" >> ~/.bashrc

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /usr/lib/jvm/java-8-oracle
RUN wget http://apache.mivzakim.net/maven/maven-3/3.5.4/binaries/apache-maven-3.5.4-bin.tar.gz
RUN tar -xvzf apache-maven-3.5.4-bin.tar.gz 
ENV PATH=/usr/lib/jvm/java-8-oracle/apache-maven-3.5.4/bin:$PATH
RUN mkdir -p SimpleSend 
RUN mkdir -p SimpleSend/src/main/java/com/microsoft/azure/eventhubs/samples/SimpleSend/

COPY SimpleSend.java SimpleSend/src/main/java/com/microsoft/azure/eventhubs/samples/SimpleSend/

COPY  pom.xml /usr/lib/jvm/java-8-oracle/SimpleSend
RUN cd /usr/lib/jvm/java-8-oracle/SimpleSend && mvn package
#RUN java -jar ReceiveByDateTime/target/receiveusingoffset-1.0.0-jar-with-dependencies.jar 


