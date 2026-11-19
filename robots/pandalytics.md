---
name: Pandalytics
operator: Domainsbot Inc.
website: https://domainsbot.com
documentation: https://domainsbot.com/network-crawler-pandalytics-kdc68dhsbd/
category: marketing
robots_txt_token: Pandalytics
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: Pandalytics
  identity: DomainsBot
last_checked: 2026-11-19
---

# Pandalytics

## Description

Pandalytics is the crawler of Domainsbot Inc. It collects public technical metadata about a
domain's homepage (HTTP status, title and description, language, detected technologies, TLS and
DNS facts) for Domainsbot's domain-intelligence and analytics products.

## Behavior

Domainsbot says Pandalytics fetches `/robots.txt` first and fetches the homepage only if the
`Pandalytics` token is allowed, then makes a single, low-rate HTTPS GET of the homepage `/`, with
no deep crawling. It uses GET requests only, with no logins, no form submissions and no JavaScript
execution. Homepages are re-crawled "on a recurring basis", with a frequency that varies by domain
and is "kept at a low per-domain rate"; no number is given. It honours `Disallow` and
`Crawl-delay`.

How long `robots.txt` is cached is not documented.

## User agents

Exact strings, one per line:

```
Pandalytics/2.0 (+https://domainsbot.com/network-crawler-pandalytics-kdc68dhsbd/)
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Pandalytics
Disallow: /
```

To allow it at a lower rate, Domainsbot gives:

```
User-agent: Pandalytics
Crawl-delay: 10
```

No other token is documented. Opt-out and block requests: crawler@domainsbot.com.

## IP ranges and verification

None published. Domainsbot says identity "is proven by request signature, not a fixed IP list;
egress IP addresses may vary". No reverse DNS hostnames or ASN are documented.

Pandalytics is a Cloudflare Verified Bot via Web Bot Auth (RFC 9421 HTTP Message Signatures,
Ed25519). Requests carry `Signature`, `Signature-Input` and `Signature-Agent` headers, with the
documented `Signature-Agent` value `"https://domainsbot.com"`. The key directory is
https://domainsbot.com/.well-known/http-message-signatures-directory: on 2026-11-19 it held one
`OKP` / `Ed25519` key without a `kid`, so a signature's `keyid` can only match the key's JWK
thumbprint. The directory's own response was signed with that key, its `keyid` being the
thumbprint.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 parses the user agent as family `Pandalytics`. Since Hyperwatch
5.7.0, `src/modules/identity.js` sets the identity `DomainsBot` signed only: a verified signature
of `https://domainsbot.com` (the `signedOnly` map, checked before the rules per family) gives
`DomainsBot` whatever the user agent. `https://domainsbot.com` is in
`src/data/webbotauth-agents.json` (robot `Pandalytics`), and its one key is in
`webbotauth-keys.json`, the same as the published directory on 2026-11-19. There is no rule for the
family `Pandalytics`: without the `webbotauth` module (off by default) or without a valid
signature, the request gets no identity. This matches Domainsbot's documentation, which publishes
no addresses or hostnames.

## Misc

- Domainsbot describes itself on the page as ICANN-accredited. The page says it was last updated
  on 2026-11-12.
- The identity is named after the operator (`DomainsBot`), not the robot.

## Sources

- https://domainsbot.com/network-crawler-pandalytics-kdc68dhsbd/ (checked 2026-11-19)
- https://domainsbot.com/.well-known/http-message-signatures-directory (checked 2026-11-19)
