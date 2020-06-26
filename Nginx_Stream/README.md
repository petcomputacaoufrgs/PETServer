Docker Image with stream configuration applied to Nginx for TCP/UDP reverse proxy  for ARM and AMD architectures.
To use this feature just add stream config files to '/opt/nginx/stream.conf.d/stream.conf'.

Example of config file: 

upstream external-database-server {
  server <IP>:<PORT>;
}

server {
  listen <PORT>;
  proxy_pass external-database-server;
}