# Docker examples for Monica

In this section you will find how to run monica with https and generate a [Let's Encrypt](https://letsencrypt.org/) certificate.

## Run with docker-compose

### Configuration (all versions)

First, copy the sample env file and update with the appropriate variable for your use case. 

```sh
cp .env.example .env
```

Open the file in an editor and update it for your own needs:

- Set `APP_KEY` to a random 32-character string. You can for instance copy and paste the output of `echo -n 'base64:'; openssl rand -base64 32`.
- Edit the `MAIL_*` settings to point to your own [mailserver](/docs/installation/mail.md).
- Set `DB_*` settings to point to your database configuration. If you don't want to set a db prefix, be careful to set `DB_PREFIX=` and not `DB_PREFIX=''` as docker will not expand this as an empty string.
- Set `DB_HOST=db` or any name of the database container you will link to.


### With nginx proxy and a self-signed certificate

- Set `VIRTUAL_HOST` and `SSL_SUBJECT` with the right domain name.
- Use a valid email for `LETSENCRYPT_EMAIL` 
- Complete `APP_URL` in your `.env` file with the right domain url

You may want to set `APP_ENV=production` to force the use of `https` scheme.

This example add a `redis` container, that can be used too, adding these variables to your `.env` file:
- `REDIS_HOST=redis`: mandatory
- `CACHE_DRIVER=redis`: to use redis as a cache table
- `QUEUE_CONNECTION=redis`: to use redis as a queue table
