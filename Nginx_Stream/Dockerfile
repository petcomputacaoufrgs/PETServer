FROM debian:stable-slim

WORKDIR /opt

RUN apt-get update && apt-get -y upgrade && \
    apt-get install -y wget libpcre3-dev build-essential libssl-dev zlib1g-dev && \
    rm -rf /var/lib/apt/lists/* && \
    wget https://nginx.org/download/nginx-1.17.2.tar.gz && \
    tar -zxvf nginx-1.*.tar.gz && \
    cd nginx-1.* && \
    ./configure --prefix=/opt/nginx --user=nginx --group=nginx --with-http_ssl_module --with-ipv6 --with-threads --with-stream --with-stream_ssl_module && \
    make && make install && \
    cd .. && rm -rf nginx-1.* && \
    adduser --system --no-create-home --disabled-login --disabled-password --group nginx && \
    mkdir /opt/nginx/conf && mkdir /opt/nginx/stream.conf.d

COPY nginx.conf /opt/nginx/conf/nginx.conf

WORKDIR /

EXPOSE 80

ENTRYPOINT ["/opt/nginx/sbin/nginx", "-g", "daemon off;"]
