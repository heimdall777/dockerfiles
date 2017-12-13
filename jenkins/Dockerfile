FROM jenkins

USER root

ARG GID=132

RUN echo "deb http://ftp.de.debian.org/debian experimental main" >> /etc/apt/sources.list \
    && echo "deb http://ftp.de.debian.org/debian unstable main" >> /etc/apt/sources.list \
    && cd /tmp \
    && curl -L -o docker-latest.tgz  https://get.docker.com/builds/Linux/x86_64/docker-latest.tgz \
    && gzip -d docker-latest.tgz \
    && tar -xvf docker-latest.tar \
    && mv /tmp/docker/docker /usr/local/bin \
    && rm -rf /tmp/docker docker-latest.tar \
    && addgroup --gid $GID docker \
    && apt-get update && apt-get install -y python3.6 nodejs \ 
    && usermod -aG staff,docker jenkins \
    && apt-get -q autoremove \
    && apt-get -q clean -y \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/*.bin

USER jenkins

VOLUME ["/var/run/docker.sock","/var/jenkins_home"]