FROM ubuntu:trusty

ARG JMAJOR=8
ARG JUPDATE=77
ARG JB=03

RUN apt-get -y update && apt-get -y install curl 

RUN curl -jkLH "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/${JMAJOR}u${JUPDATE}-b${JB}/jdk-${JMAJOR}u${JUPDATE}-linux-x64.tar.gz" > /opt/jdk-${JMAJOR}u${JUPDATE}-linux-x64.tar.gz \
 		&& tar zxvf /opt/jdk-${JMAJOR}u${JUPDATE}-linux-x64.tar.gz -C /opt \
 		&& rm /opt/jdk-${JMAJOR}u${JUPDATE}-linux-x64.tar.gz

ENV JAVA_HOME /opt/jdk1.${JMAJOR}.0_${JUPDATE}