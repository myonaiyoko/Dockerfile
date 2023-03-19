# cat Dockerfile
FROM almalinux:9

RUN dnf -y update && \
    dnf install -y java-17-openjdk && \
    dnf install -y git-all && \
    dnf install -y wget && \
    mkdir -p /src/java && \
    mkdir -p /opt/maven && \
    cd /opt/maven && \
    wget https://archive.apache.org/dist/maven/maven-3/3.9.0/binaries/apache-maven-3.9.0-bin.tar.gz && \
    tar zxvf apache-maven-3.9.0-bin.tar.gz && \
    ln -s /opt/maven/apache-maven-3.9.0 apache-maven && \
    rm -fr apache-maven-3.9.0-bin.tar.gz

ENV PATH $PATH:/opt/maven/apache-maven/bin
EXPOSE 8080
