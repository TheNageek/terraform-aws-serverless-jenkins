FROM jenkins/jenkins:lts-jdk17

# Configuration as Code (CasC)
ENV CASC_JENKINS_CONFIG /usr/share/jenkins/ref/jenkins.yaml
COPY files/jenkins.yaml /usr/share/jenkins/ref/jenkins.yaml

# Indicate that this Jenkins installation is fully configured. Otherwise a banner will
# appear prompting the user to install additional plugins, which may be inappropriate.
RUN echo 2.0 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state

# Groovy configuration
COPY files/InitialConfig.groovy /usr/share/jenkins/ref/init.groovy.d/InitialConfig.groovy

# Install plugins
COPY files/plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt