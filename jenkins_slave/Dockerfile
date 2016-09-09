FROM javabase

RUN apt-get -y update && apt-get -y install git openssh-server

ENV PATH $JAVA_HOME/bin:$PATH
ENV JENKINS_HOME /opt/jenkins

RUN sed -i 's|session    required     pam_loginuid.so|session    optional     pam_loginuid.so|g' /etc/pam.d/sshd &&\
    mkdir -p /var/run/sshd

RUN adduser --quiet --disabled-password --gecos "" jenkins &&\
    echo "jenkins:jenkins" | chpasswd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]