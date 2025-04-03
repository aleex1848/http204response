# http204response
This is nginx webserver which always returns HTTP 204.
It's intended to be used as a fake-backend when using modsecurity container as WAF for multiple apps.

An example of this approach using Traefik can be found here:
https://community.traefik.io/t/owasp-modsecurity/16810/2

the modsecurity-backend is intended to be the app which should be protected.
but if you want to use one modsecurity container for multiple apps you have to set a fake backend.
the backends usually used for that (like whoami in the given example) are restricted in max_body_size.
So when you try to upload a larger file to your protected app it will fail because the fake backend will 
respone an error.

This container provides an nginx webserver with max_body_size of 2GB, which always returns HTTP 204.

Docker Build

docker build -t your-tag .



