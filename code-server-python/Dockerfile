FROM linuxserver/code-server

RUN bash -c ' \
    apt-get update && \
    apt-get install -y --no-install-recommends python3.8 python3-pip && \
    pip install --no-cache-dir Scrapy && \
    apt-get clean && \
    rm -fr /var/lib/apt/lists \
    '