---
name: Amazonbot
operator: Amazon
website: https://www.amazon.com
documentation: https://developer.amazon.com/amazonbot
category: ai-training
robots_txt_token: Amazonbot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://developer.amazon.com/amazonbot/ip-addresses/
  hostnames: []
hyperwatch:
  family: Amazonbot
  identity: Amazonbot
last_checked: 2026-10-15
---

# Amazonbot

## Description

Amazonbot is Amazon's web crawler. Amazon says it "is used to improve our products and services"
and "may be used to train Amazon AI models". Amazon runs two other agents with their own tokens:
Amzn-SearchBot and Amzn-User.

## Behavior

Amazon documents the same rules for Amazonbot, Amzn-SearchBot and Amzn-User:

- They fetch `robots.txt` per host (`example.com/robots.txt`, `site.example.com/robots.txt`) or
  use a cached copy from the last 30 days. When the file can't be fetched, they act as if it does
  not exist.
- They honor `rel=nofollow` on links and the robots meta values `noarchive` ("do not use the page
  for model training"), `noindex` and `none`.
- They do not support `Crawl-delay`.
- Changes to the settings for each agent may take about 24 hours to apply.

Crawl rate and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Amazonbot/0.1) Chrome/W.X.Y.Z Safari/537.36
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_1) AppleWebKit/600.2.5 (KHTML, like Gecko) Version/8.0.2 Safari/600.2.5 (Amazonbot/0.1; +https://developer.amazon.com/support/amazonbot)
```

The first is the current example, where `W.X.Y.Z` stands for a Chrome version. The second is the
example from the archived January 2025 version of the page.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Amazonbot
Disallow: /
```

Amazonbot obeys `User-agent` and `Allow`/`Disallow`. Blocking it does not block Amzn-SearchBot or
Amzn-User: each token is set separately.

## IP ranges and verification

Amazon publishes the addresses at https://developer.amazon.com/amazonbot/ip-addresses/. It is an
HTML page with the list in a code block: a JSON object with `creationTime` and a `prefixes` array of
`{"ipv4Prefix": ...}` objects holding single addresses without a prefix length. On 2026-10-15 it
held 1,292 IPv4 addresses, with `creationTime` 2026-09-08. No IPv6.

The archived January 2025 version of the page described a forward-confirmed reverse DNS check: the
name must be a subdomain of `crawl.amazonbot.amazon` and must resolve back to the same address. The
current page no longer mentions reverse DNS, and three addresses of the published list looked up on
2026-10-15 had `*.compute-1.amazonaws.com` names. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Amazonbot` for both strings above. In
`src/modules/identity.js`, Hyperwatch sets the identity `Amazonbot` when the reverse DNS hostname
(not forward-confirmed) ends with `.crawl.amazonbot.amazon`, or when the address is in
`src/data/amazonbot-ips.json`. That file is updated by hand (there is no fetch script); on
2026-10-15 it held the same 1,292 addresses as the published list. The hostname suffix comes from
Amazon's older documentation, and the check does not use the forward lookup Amazon described.

## Misc

- Amzn-SearchBot (search experiences such as Alexa) and Amzn-User (fetches on a user's behalf)
  have their own files.
- Amazon's contact for content owners is amazonbot@amazon.com.
- Amazon Quick's web crawler, which customers point at sites, is a separate agent
  (`amazon-Quick-on-behalf-of-<UUID>`).

## Sources

- https://developer.amazon.com/amazonbot (checked 2026-10-15)
- https://developer.amazon.com/amazonbot/ip-addresses/ (checked 2026-10-15)
- https://web.archive.org/web/20250101102835/https://developer.amazon.com/amazonbot (checked 2026-10-15)
