**DEVELOPER INSTRUCTIONS:**

- Update module name in go.mod
- Update dependencies to latest versions
- Update name and year in license
- Customize configuration and Caddyfile parsing
- Update godocs / comments (especially provider name and nuances)
- Update README and remove this section

---

RFC-2136 module for Caddy
===========================

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with \<PROVIDER\>.

## Caddy module name

```
dns.providers.rfc_2136
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
	"module": "acme",
	"challenges": {
		"dns": {
			"provider": {
				"name":             "rfc_2136",
				"api_token":        "YOUR_PROVIDER_API_TOKEN",
				"rfc2136_server":   "YOUR_PROVIDER_RFC2136_SERVER_IP",
				"rfc2136_port":     "YOUR_PROVIDER_DNS_PORT",
				"rfc2136_name":     "YOUR_KEY_RECORD_NAME",
				"rfc2136_secret":   "YOUR_KEY_RECORD_SECRET",
				"rfc2136_algorithm":"YOUR_PROVIDER_ALGORITHM"
			}
		}
	}
}
```

or with the Caddyfile:

```
# globally
{
	acme_dns provider_name ...
}
```

```
# one site
tls {
	dns provider_name ...
}
```
