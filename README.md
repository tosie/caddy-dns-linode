# Linode DNS module for Caddy

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with Hetzner accounts.

## Caddy module name

```
dns.providers.linode
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
  "module": "acme",
  "challenges": {
    "dns": {
      "provider": {
        "name": "linode",
        "api_token": "YOUR_LINODE_PERSONAL_ACCESS_TOKEN"
      }
    }
  }
}
```

or with the Caddyfile:

```
your.domain.com {
  respond "Hello World"	# replace with whatever config you need...
  tls {
    dns linode {env.YOUR_LINODE_PERSONAL_ACCESS_TOKEN}
  }
}
```

You can replace `{env.YOUR_LINODE_PERSONAL_ACCESS_TOKEN}` with the actual auth token if you prefer to put it directly in your config instead of an environment variable.

## Authenticating

See [the associated README in the libdns package](https://github.com/tosie/libdns-linode#authenticating) for important information about credentials.
