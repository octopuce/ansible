# roles/turnserver

Install and configure a turnserver.

It also adds a cron to start the coturn server every 5 minutes if
needed, as coturn is known to crash after a few minutes.

## Configuration

The coturn template expects a `coturn_secret` variable to be defined.
The value should be a 32-bytes hex-encoded random string.  You might
generate one using `openssl rand -hex 32`.

## Limitations

- Only tested on Debian Stretch.
- Only support coturn package.
- The configuration is written according to NextCloud Talk's
  recommendations. It might be not suited for other uses (BBB).

## Resources

- https://nextcloud-talk.readthedocs.io/en/latest/TURN/
