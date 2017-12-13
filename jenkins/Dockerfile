FROM jenkins

USER root

ARG GID=132

RUN echo "deb http://ftp.de.debian.org/debian experimental main" >> /etc/apt/sources.list \
    && echo "deb http://ftp.de.debian.org/debian unstable main" >> /etc/apt/sources.list \
    && apt-get update && apt-get install -y python3.6 nodejs docker.io \ 
    && usermod -aG staff,docker jenkins \
    && apt-get -q autoremove \
    && apt-get -q clean -y \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/*.bin

USER jenkins

VOLUME ["/var/run/docker.sock","/var/jenkins_home"]