FROM javabase

ARG MAJOR=2
ARG MINOR=7
ARG PATCH=3

RUN apt-get -y update && apt-get -y install git wget

ENV PATH $JAVA_HOME/bin:$PATH

RUN curl -jkL "http://repo.jenkins-ci.org/public/org/jenkins-ci/main/jenkins-war/${MAJOR}.${MINOR}.${PATCH}/jenkins-war-${MAJOR}.${MINOR}.${PATCH}.war" > /opt/jenkins.war && chmod 644 /opt/jenkins.war

ENV JENKINS_HOME /opt/jenkins

COPY plugins.txt ${JENKINS_HOME}/

RUN mkdir $JENKINS_HOME/plugins && \
wget -i ${JENKINS_HOME}/plugins.txt -P ${JENKINS_HOME}/plugins/

EXPOSE 8080

ENTRYPOINT ["java", "-Djenkins.install.runSetupWizard=false", "-jar", "/opt/jenkins.war"]