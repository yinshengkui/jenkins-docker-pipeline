FROM jenkinsci/jenkins:2.41

USER root

#RUN  curl -sL https://deb.nodesource.com/setup_7.x | bash - && apt-get install -y \
#  docker.io \
#  nodejs \
#  && usermod -a -G staff jenkins

USER jenkins
ENV JAVA_OPTS='-Djenkins.install.runSetupWizard=false -Dhudson.model.DirectoryBrowserSupport.CSP='

ADD JENKINS_HOME /usr/share/jenkins/ref

HEALTHCHECK CMD curl --fail http://localhost:8080/tcpSlaveAgentListener/ || exit 1

COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN xargs -a /usr/share/jenkins/plugins.txt /usr/local/bin/install-plugins.sh
