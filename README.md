## About

`waf-runner` builds and runs a WAF container locally. It's good for testing WAFs. `waf` folder containes `Dockerfile`s and related files for sample WAFs. See [this blog post](https://jreisinger.github.io/blog2/posts/working-with-waf-containers/) for more.

## Installation

Copy `waf-runner` to your bin folder (or some other folder on your `PATH`) and make it executable:

```
cp waf-runner ~/bin/
chmod u+x ~/bin/waf-runner
```

## Sample usage

Start a testing WAF and a testing backend web server on localhost:

```
cd waf/nginx/modsecurity
waf-runner -i kennethreitz/httpbin -s .
```
