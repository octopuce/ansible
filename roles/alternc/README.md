# roles/alternc

Post configuration of AlternC, for the Octopuce common setup.

AlternC is designed to work natively with Apache2. At Octopuce, we
usually put Nginx as a frontend server, and use Apache2 as a backend
server, so we change a bit the template to reflect the fact apache
does not bind to `0.0.0.0:80`.

We also change the templates for PHP as the packaged config uses
`ProxyPassMatch` directive, which does not work with Stretch's
Apache2.

## Configuration / Variables

- `alternc_apache_addr`: The listen address of the apache
  service. Defaults to `0.0.0.0`.
- `alternc_apache_port`: The listen port of the apache
  service. Defaults to `80`.

Those variables will affect the `proxy_pass` directive in nginx config
and templates, along with the `<VirtualHost>` directive in Apache
templates.

## Limitations

- Only tested on Debian Stretch, with alternc-3.1.1,
  alternc-nginx-ssl-3.1.1 and alternc-php-fpm-3.1.1.
- May cause incompatibilities with other AlternC modules
