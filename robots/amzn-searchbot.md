---
name: Amzn-SearchBot
operator: Amazon
website: https://www.amazon.com
documentation: https://developer.amazon.com/amazonbot
category: ai-search
robots_txt_token: Amzn-SearchBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://developer.amazon.com/amazonbot/searchbot-ip-addresses/
  hostnames: []
hyperwatch:
  family: Amzn-SearchBot
  identity: Amazon SearchBot
last_checked: 2026-10-15
---

# Amzn-SearchBot

## Description

Amzn-SearchBot is Amazon's crawler for search. Amazon says it "is used to improve search
experiences in Amazon products and services" and that allowing it makes content "eligible to appear
in search experiences such as Alexa". Amazon states it "does not crawl content for generative AI
model training".

## Behavior

Amazon documents the same rules for Amazonbot, Amzn-SearchBot and Amzn-User:

- They fetch `robots.txt` per host or use a cached copy from the last 30 days. When the file can't
  be fetched, they act as if it does not exist.
- They honor `rel=nofollow` on links and the robots meta values `noarchive`, `noindex` and `none`.
- They do not support `Crawl-delay`.
- Changes may take about 24 hours to apply.

Crawl rate and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Amzn-SearchBot/0.1) Chrome/W.X.Y.Z Safari/537.36
```

This is Amazon's example; `W.X.Y.Z` stands for a Chrome version.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Amzn-SearchBot
Disallow: /
```

Amazon says that if `robots.txt` doesn't mention Amzn-SearchBot "but allow[s] other search bots",
Amzn-SearchBot follows the directives given to other search bots. Amazon does not say which tokens
count as search bots. Blocking Amazonbot does not block Amzn-SearchBot.

## IP ranges and verification

Amazon publishes the addresses at https://developer.amazon.com/amazonbot/searchbot-ip-addresses/.
It is an HTML page with the list in a code block: a JSON object with `creationTime` and a
`prefixes` array of `{"ip_prefix": ...}` objects (a different key from the Amazonbot list). On
2026-10-15 it held 816 IPv4 prefixes, all `/32`, with `creationTime` 2026-09-08. No IPv6.

No reverse DNS hostname or ASN is documented for Amzn-SearchBot.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Amzn-SearchBot`. In `src/modules/identity.js`,
Hyperwatch sets the identity `Amazon SearchBot` when the reverse DNS hostname (not
forward-confirmed) ends with `.crawl.amazonbot.amazon`, or when the address is in
`src/data/amazon-searchbot-ips.json`. That file is updated by hand; on 2026-10-15 it held the same
816 prefixes as the published list. The hostname suffix is not documented for Amzn-SearchBot: it
comes from Amazon's older Amazonbot documentation.

## Misc

- See Amazonbot and Amzn-User, documented on the same page.
- Amazon's contact for content owners is amazonbot@amazon.com.

## Sources

- https://developer.amazon.com/amazonbot (checked 2026-10-15)
- https://developer.amazon.com/amazonbot/searchbot-ip-addresses/ (checked 2026-10-15)
