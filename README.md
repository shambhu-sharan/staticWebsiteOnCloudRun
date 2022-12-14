# staticWebsiteOnCloudRun
<pre>
Create a new Dockerfile inside the website directory:

$ cat Dockerfile
FROM nginx
COPY html /usr/share/nginx/html
COPY nginx/default.conf /etc/nginx/conf.d/default.conf
In this Dockerfile we are just telling Docker to create a new container based on the nginx container and we are adding our html directory (that contains our index.html) plus an nginx configuration file that we will create next.

In the nginx directory create a default.conf file (note how we listen on port 8080):

$ cat nginx/default.conf
server {
listen       8080;
server_name  localhost;
location / {
root   /usr/share/nginx/html;
index  index.html index.htm;
}
# redirect server error pages to the static page /50x.html
error_page   500 502 503 504  /50x.html;
location = /50x.html {
root   /usr/share/nginx/html;
}
}
After all this, you should have this directory structure:

$ tree
.
├── Dockerfile
├── html
│   └── index.html
└── nginx
    └── default.conf

</pre>
