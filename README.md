## About

`waf-runner` builds and runs a WAF container locally. It's good for testing WAFs. `waf` folder containes `Dockerfile` and related files for sample WAFs.

## Installation

Copy `waf-runner` to your bin folder and make it executable:

```
make install
```

## Sample usage

Start a testing backend web server and a testing WAF on localhost:

```
$ waf-runner -i kennethreitz/httpbin waf/nginx/modsecurity
--> Create directories for WAF logs in /tmp/var/log
mkdir: created directory '/tmp/var/log'
mkdir: created directory '/tmp/var/log/nginx'
--> Create temporary directory
/var/folders/8d/49xspl216vqf52y6b_s_y9x00000gn/T/tmp.JwTCfMMJr6
--> Create /var/folders/8d/49xspl216vqf52y6b_s_y9x00000gn/T/tmp.JwTCfMMJr6/docker-compose.yaml
--> Copy recursively all files from waf/nginx/modsecurity to /var/folders/8d/49xspl216vqf52y6b_s_y9x00000gn/T/tmp.JwTCfMMJr6
--> Build and run containers for WAF and web server
Creating network "tmpjwtcfmmjr6_default" with the default driver
Building testing-waf
Creating testing-webserver ... done
Creating testing-waf       ... done
--> Check WAF is up and proxying requests
CONTAINER ID   IMAGE                       COMMAND                  CREATED         STATUS         PORTS                  NAMES
b2f91c819cac   tmpjwtcfmmjr6_testing-waf   "nginx -g 'daemon of…"   6 seconds ago   Up 5 seconds   0.0.0.0:80->80/tcp     testing-waf
2e055fb64404   kennethreitz/httpbin        "gunicorn -b 0.0.0.0…"   6 seconds ago   Up 5 seconds   0.0.0.0:8080->80/tcp   testing-webserver
--> WAF container is up and running (hit Ctrl-C to quit)
==> /tmp/var/log/modsec_audit.log <==

==> /tmp/var/log/nginx/access.log <==
172.19.0.1 - - [03/Mar/2022:11:39:58 +0000] "GET / HTTP/1.1" 200 9593 "-" "curl/7.77.0" "-"

==> /tmp/var/log/nginx/error.log <==
```
