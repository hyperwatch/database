---
name: SenderBot
operator: Sender Online Marketing GmbH
website: https://sender-marketing.de
documentation: https://sender-marketing.de/bot/
category: marketing
robots_txt_token: SenderBot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: SenderBot
  identity: null
last_checked: 2026-10-15
---

# SenderBot

## Description

SenderBot is run by Sender Online Marketing GmbH, a German marketing company. It collects links and
the main text of pages for internal analysis in customer projects. The text is later searched for
mentions of specific brands and companies. The operator says it does not publish the texts, pass
them to third parties, or use them to train AI models.

## Behavior

By default the robot fetches at most one page per second per site. It also caps the number of
pages per site per day, without giving the number. It slows down on `429` or `403` responses and
pauses a site after repeated rejections. It follows `Crawl-delay`.

It honors robots meta tags and the `X-Robots-Tag` header. With `noindex` it does not store the
page text. It respects `nofollow` and `rel="nofollow"` links. `robots.txt` is cached, so changes
take effect within 24 hours. JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; SenderBot/1.0; Sender Online Marketing GmbH; +https://sender-marketing.de/bot)
```

The operator documents the same string.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: SenderBot
Disallow: /
```

`Crawl-delay` is supported. The operator also accepts opt-out requests by email, even for sites
without a `robots.txt`.

## IP ranges and verification

None published. No IP list, reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `SenderBot`. Hyperwatch has no identity
for it, since there is no way to verify it.

## Misc

The company's address and representatives are in its legal notice at
https://sender-marketing.de/impressum/.

## Sources

- https://sender-marketing.de/bot/ (checked 2026-10-15)
