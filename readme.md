# docker-nginx-file-static-server
Creating a static file server with docker.

# Requirements
You must install the docker before you launch a server.
Please refer the official documenation at https://docs.docker.com/engine/install/ubuntu/

# nginx.conf
```
user  nginx;
worker_processes  1;

error_log  /var/log/nginx/error.log warn;
pid        /var/run/nginx.pid;

events {
    worker_connections  1024;
}

http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;
    access_log off;
    sendfile        on;
    keepalive_timeout  65;
    gzip  on;
    include /etc/nginx/conf.d/*.conf;
    autoindex on;
}
```


# Run
```
wget blah
docker run -v /path/to/nginx.conf:/etc/nginx/nginx.conf -v /path/to/share:/usr/share/nginx/html:ro -p 80:80 -d nginx
```


## Example
```
docker run -v /home/sweetchip/nginx.conf:/etc/nginx/nginx.conf -v /home/sweetchip/static:/usr/share/nginx/html:ro -p 80:80 -d nginx
```

# Checking a web server
```
curl http://localhost/
```
Check a result after above command executed




