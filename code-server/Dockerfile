FROM linuxserver/code-server

ARG JAVA_VERSION=11
ARG JAVA_RELEASE=JDK

RUN bash -c ' \
    set -euxo pipefail && \
    apt-get update && \
    pkg="openjdk-$JAVA_VERSION"; \
    if [ "$JAVA_RELEASE" = "JDK" ]; then \
        pkg="$pkg-jdk-headless"; \
    else \
        pkg="$pkg-jre-headless"; \
    fi; \
    apt-get install -y --no-install-recommends "$pkg" python3.8 python3-pip wget tree nodejs npm && \
    pip install --no-cache-dir Scrapy && \
    apt-get clean && \
    rm -fr /var/lib/apt/lists \
    '

RUN echo "export JAVA_HOME=/usr" >> /etc/profile.d/java.sh

ENV JAVA_HOME=/usr

# Install maven 3.8.5
RUN wget --no-verbose -O /tmp/apache-maven-3.8.5-bin.tar.gz https://downloads.apache.org/maven/maven-3/3.8.5/binaries/apache-maven-3.8.5-bin.tar.gz && \
    tar xzf /tmp/apache-maven-3.8.5-bin.tar.gz -C /opt/ && \
    ln -s /opt/apache-maven-3.8.5 /opt/maven && \
    ln -s /opt/maven/bin/mvn /usr/local/bin  && \
    rm -f /tmp/apache-maven-3.8.5-bin.tar.gz

ENV MAVEN_HOME /opt/maven