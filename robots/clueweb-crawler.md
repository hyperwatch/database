---
name: ClueWeb-Crawler
operator: Carnegie Mellon University (Language Technologies Institute)
website: https://www.lti.cs.cmu.edu
documentation: https://boston.lti.cs.cmu.edu/CMU-ClueWeb-Crawler/
category: research
robots_txt_token: ClueWeb-Crawler
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: ClueWeb-Crawler
  identity: null
last_checked: 2026-10-15
---

# ClueWeb-Crawler

## Description

ClueWeb-Crawler is an academic research crawler run by Professor Chenyan Xiong's research group at
the Language Technologies Institute of Carnegie Mellon University. CMU states it is for "academic
research only". The name follows the ClueWeb web corpora built at CMU (ClueWeb09, ClueWeb12,
ClueWeb22).

## Behavior

- It fetches public, unauthenticated pages, HTML and static resources. It does not crawl private or
  paywalled content, forms, carts, POST endpoints, user accounts or dashboards.
- CMU describes "conservative per-host rate limiting" and automatic back-off on 429 and 503
  responses. No numeric crawl rate is documented.
- It honors `robots.txt` and `Crawl-delay`.
- JavaScript rendering is not documented. How often `robots.txt` is re-read is not documented.

## User agents

Exact strings, one per line:

```
ClueWeb-Crawler/1.0 (+https://boston.lti.cs.cmu.edu/CMU-ClueWeb-Crawler/; mailto:cmu-clueweb-crawler@andrew.cmu.edu)
```

This matches the string on CMU's crawler page.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: ClueWeb-Crawler
Disallow: /
```

CMU says it "honors all robots.txt directives", including `Crawl-delay`. The token is not stated
explicitly on the page; `ClueWeb-Crawler` is the product name in the user agent. CMU also offers an
opt-out form (https://forms.gle/qc4QRHHcwLzrDyBU8) and says opt-outs are "honored promptly and
permanently".

## IP ranges and verification

None published. CMU's page only says the crawler comes from the "CMU SCS IP range" (School of
Computer Science), without listing ranges, hostnames or an ASN.

## Hyperwatch

`@hyperwatch/useragent` returns the family `ClueWeb-Crawler`. `src/modules/identity.js` has no rule
for it, so it gets no identity.

## Misc

- Contact: cmu-clueweb-crawler@andrew.cmu.edu.
- CMU says data is collected for research only and that incidentally encountered personal data is
  never used for identification or tracking.

## Sources

- https://boston.lti.cs.cmu.edu/CMU-ClueWeb-Crawler/ (checked 2026-10-15)
- https://arxiv.org/pdf/2211.15848 (checked 2026-10-15)
- https://crawlconsole.com/web-crawlers/clueweb-crawler (checked 2026-10-15)
