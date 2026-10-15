---
name: BitMoversBot
operator: Byte Dev Limited
website: https://bitmovers.co.uk
documentation: https://bitmovers.co.uk/crawler/2dawcqc7
category: research
robots_txt_token: BitMoversBot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: BitMoversBot
  identity: null
last_checked: 2026-10-15
---

# BitMoversBot

## Description

BitMoversBot is described by its operator as "a small research crawler run by Byte Dev Limited
from the UK". It maps how sites link to each other, which technologies they use and what they are
about, and keeps a searchable index of that text.

## Behavior

From the operator's page:

- It mainly reads home pages and pages such as contact and about.
- It does not fill in forms, log in or bypass protections.
- It requests at most one page per second from any one site, backs off when a site signals it is
  busy, and its total request rate is capped.
- It honors `Crawl-delay` and rechecks `robots.txt` at least once a day.
- Removal requests by email, with the site address, are handled "within two working days".

JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; BitMoversBot/1.0; +https://bitmovers.co.uk/crawler/2dawcqc7)
```

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: BitMoversBot
Disallow: /
```

To slow it down instead, the operator suggests `Crawl-delay: 10`.

## IP ranges and verification

None published. No IP list, reverse DNS names or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `BitMoversBot`. `src/modules/identity.js` has no rule
for it, so Hyperwatch sets no identity.

## Misc

Nothing else documented.

## Sources

- https://bitmovers.co.uk/crawler/2dawcqc7 (checked 2026-10-15)
