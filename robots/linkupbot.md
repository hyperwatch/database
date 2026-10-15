---
name: LinkupBot
operator: Linkup
website: https://www.linkup.so
documentation: https://www.linkup.so/bot
category: ai-search
robots_txt_token: LinkupBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://www.linkup.so/linkupbot-ips.txt
  hostnames: []
hyperwatch:
  family: LinkupBot
  identity: Linkup
last_checked: 2026-10-15
---

# LinkupBot

## Description

LinkupBot is the web crawler of Linkup. It finds and fetches public web pages for Linkup's search
index, which provides search and web grounding for AI applications.

## Behavior

Linkup says LinkupBot respects applicable `robots.txt` rules and that crawling is allowed by
default when no rule forbids it. Rules apply per host, protocol and port, so subdomains may need
their own file. Allowing LinkupBot through a firewall does not override `robots.txt`.

Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` caching are not
documented. Reports go to bot@linkup.so.

## User agents

Exact strings, one per line:

```
LinkupBot/1.0 (LinkupBot for web indexing; https://linkup.so/bot; bot@linkup.so)
```

The operator documents the same string with `https://www.linkup.so/bot`:

```
LinkupBot/1.0 (LinkupBot for web indexing; https://www.linkup.so/bot; bot@linkup.so)
```

## Observed HTTP headers

Only header signatures are available (they keep `accept`, `accept-language` and `dnt`), from fewer than 10 distinct signatures seen on 2026-10-15:

- `accept`: `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8`
- `accept-language`: `en-us,en-gb,en;q=0.7,*;q=0.3`
- `dnt`: never sent

## Blocking with robots.txt

```
User-agent: LinkupBot
Disallow: /
```

No other tokens or special rules are documented.

## IP ranges and verification

Linkup publishes its source ranges at https://www.linkup.so/linkupbot-ips.txt, a plain text file
with one CIDR per line. On 2026-10-15 it held 1 range (`35.198.113.100/32`). Linkup says the list
may change and should be fetched periodically. It recommends checking both the source address and
the `LinkupBot` token. No reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Reverse DNS hostnames:

- `*.bc.googleusercontent.com` (forward-confirmed, addresses in the published ranges)

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `LinkupBot`. Hyperwatch sets the
identity `Linkup` when the client address is in `35.198.113.100/32`, hard-coded in
`src/modules/identity.js` from Linkup's list.

## Misc

Nothing else documented.

## Sources

- https://linkup.so/bot (checked 2026-10-15)
- https://www.linkup.so/linkupbot-ips.txt (checked 2026-10-15)
