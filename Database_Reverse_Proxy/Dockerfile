FROM petcompufrgs/nginx-stream:1.0

COPY stream.conf /opt/nginx/stream.conf.d/stream.conf

WORKDIR /

EXPOSE 5432

ENTRYPOINT ["/opt/nginx/sbin/nginx", "-g", "daemon off;"]
