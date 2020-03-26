# NGINX reverse proxy based on host-headers

A simple setup to demonstrate the configuration of reverse proxy based on host headers.

This setup uses [docker-compose](https://docs.docker.com/compose/), thereby also requires a running Docker environment.

## Running

Simply start the enviornment using `docker-compose up`:
```bash
> $ docker-compose up
Starting nginx_hh_demo_website1_1      ... done
Starting nginx_hh_demo_reverse_proxy_1 ... done
Starting nginx_hh_demo_website2_1      ... done
Attaching to nginx_hh_demo_website1_1, nginx_hh_demo_website2_1, nginx_hh_demo_reverse_proxy_1
```

Query the websites directly, bypassing the proxy for now:

```bash
> $ curl http://localhost:8881
<h1>Website 1!</h1>

> $ curl http://localhost:8882
<h1>Website 2!</h1>%
```

Query the proxy, without host headers:

```bash
> $ curl http://localhost:8888
<h1>Website Reverse Proxy!</h1>
```

Finally, query the proxy, using host headers:

```bash
> $ curl http://localhost:8888 --header 'Host: website1'
<h1>Website 1!</h1>

> $ curl http://localhost:8888 --header 'Host: website2'
<h1>Website 2!</h1>
```