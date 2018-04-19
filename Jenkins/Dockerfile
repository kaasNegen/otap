FROM jenkins:2.46.3

# Install plugins
# Doesn't work properly, see the issues below for explanation. If the issues are fixed it can be enabled again.
# https://github.com/jenkinsci/docker/issues/494
# https://github.com/jenkinsci/docker/pull/495
#RUN /usr/local/bin/install-plugins.sh maven-plugin:2.15.1 git:3.3.0 sonar:2.6.1 workflow-aggregator:2.5 gatling:1.2.2 blueocean:1.0.1 pipeline-stage-view:2.8 

# Maven Integration Plugin
# Git plugin
# SonarQube Scanner for Jenkins
# Pipeline
# Gatling Jenkins Plugin
# Blue Ocean
# Pipeline: Stage View Plugin

# Disable plugin dialog
RUN echo 2.0 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state

# Install Maven
# Not so good from a security perspective
USER root 

ARG MAVEN_VERSION=3.3.9
ARG BASE_URL=https://apache.osuosl.org/maven/maven-3/${MAVEN_VERSION}/binaries

RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && curl -fsSL -o /tmp/apache-maven.tar.gz ${BASE_URL}/apache-maven-$MAVEN_VERSION-bin.tar.gz \
  && tar -xzf /tmp/apache-maven.tar.gz -C /usr/share/maven --strip-components=1 \
  && rm -f /tmp/apache-maven.tar.gz \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven

