## About

`waf-runner` builds and runs a WAF container locally. It's good for testing WAFs. `waf` folder containes `Dockerfile` and related files for sample WAFs.

## Installation

Copy `waf-runner` to your bin folder and make it executable:

```
make install
```

## Sample usage

Start a testing WAF and a testing backend web server on localhost:

```
waf-runner -i kennethreitz/httpbin waf/nginx/modsecurity
```
