---
name: Amzn-User
operator: Amazon
website: https://www.amazon.com
documentation: https://developer.amazon.com/amazonbot
category: ai-assistant
robots_txt_token: Amzn-User
respects_robots_txt: partial
verification:
  method: ip-list
  ip_list: https://developer.amazon.com/amazonbot/live-ip-addresses/
  hostnames: []
hyperwatch:
  family: Amzn-User
  identity: Amazon User
last_checked: 2026-10-15
---

# Amzn-User

## Description

Amzn-User fetches pages for Amazon users. Amazon says it "supports user actions, such as
responding to Alexa queries that require up-to-date information": when a customer asks a question,
it "may fetch live information from the web" on the user's behalf. Amazon states it "does not crawl
content for generative AI model training".

## Behavior

"Because actions taken by Amzn-User can be initiated by a user, it may not follow all robots.txt
directives." For its automated requests, Amazon documents the same rules as for Amazonbot and
Amzn-SearchBot:

- `robots.txt` is fetched per host or taken from a cached copy from the last 30 days. When it can't
  be fetched, the agent acts as if it does not exist.
- `rel=nofollow` and the robots meta values `noarchive`, `noindex` and `none` are honored.
- `Crawl-delay` is not supported.
- Changes may take about 24 hours to apply.

Request rate and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Amzn-User/0.1) Chrome/W.X.Y.Z Safari/537.36
```

This is Amazon's example; `W.X.Y.Z` stands for a Chrome version.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Amzn-User
Disallow: /
```

User-initiated fetches may not follow all directives (see Behavior). Blocking Amazonbot does not
block Amzn-User.

## IP ranges and verification

Amazon publishes the addresses at https://developer.amazon.com/amazonbot/live-ip-addresses/. It is
an HTML page with the list in a code block: a JSON object with `creationTime` and a `prefixes`
array of `{"ipv4Prefix": ...}` objects holding single addresses without a prefix length. On
2026-10-15 it held 1,023 IPv4 addresses, with `creationTime` 2025-11-04. No IPv6.

No reverse DNS hostname or ASN is documented for Amzn-User.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Amzn-User`. In `src/modules/identity.js`, Hyperwatch
sets the identity `Amazon User` when the reverse DNS hostname (not forward-confirmed) ends with
`.crawl.amazonbot.amazon`, or when the address is in `src/data/amazon-user-ips.json`. That file is
updated by hand; on 2026-10-15 it held the same 1,023 addresses as the published list. The hostname
suffix is not documented for Amzn-User: it comes from Amazon's older Amazonbot documentation.

## Misc

- See Amazonbot and Amzn-SearchBot, documented on the same page.
- Amazon's contact for content owners is amazonbot@amazon.com.

## Sources

- https://developer.amazon.com/amazonbot (checked 2026-10-15)
- https://developer.amazon.com/amazonbot/live-ip-addresses/ (checked 2026-10-15)
