# TransIP module for Caddy

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with TransIP accounts.

## Caddy module name

```
dns.providers.transip
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
	"module": "acme",
	"challenges": {
		"dns": {
			"provider": {
				"name": "transip",
				"username": "{env.YOUR_TRANSIP_USERNAME}",
				"privatekey_path": "{env.YOUR_TRANSIP_PRIVATEKEY_PATH}"
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
		dns transip {env.YOUR_TRANSIP_USERNAME, env.YOUR_TRANSIP_PRIVATEKEY_PATH}
	}
}
```

You can replace `{env.YOUR_TRANSIP_USERNAME}` and `{env.YOUR_TRANSIP_PRIVATEKEY_PATH}` with the actual username and path to private key file if you prefer to put it directly in your config instead of an environment variable.

## Authenticating

See [the associated README in the libdns package](https://github.com/libdns/transip) for important information about credentials.
