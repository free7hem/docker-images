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
    apt-get install -y --no-install-recommends "$pkg" && \
    apt-get clean && \
    rm -fr /var/lib/apt/lists \
    '

RUN echo "export JAVA_HOME=/usr" >> /etc/profile.d/java.sh

ENV JAVA_HOME=/usr