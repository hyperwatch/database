---
name: Baiduspider
operator: Baidu
website: https://www.baidu.com
documentation: https://help.baidu.com/question?prod_id=99&class=476&id=2996
category: search-engine
robots_txt_token: Baiduspider
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames:
    - .baidu.com
    - .baidu.jp
hyperwatch:
  family: Baiduspider
  identity: Baidu
last_checked: 2026-10-15
---

# Baiduspider

## Description

Baiduspider is the crawler of Baidu, the Chinese search engine. It fetches pages to build the index
of Baidu's web search. This file also covers `Baiduspider-image` (Baidu image search) and
`Baiduspider-render`.

## Behavior

Baidu says Baiduspider keeps crawling new and updated pages, and adjusts its crawl based on server
capacity, site quality and how often the site changes. It obeys the robots meta tags: a page can
be indexed without a cached snapshot shown in results. After a `robots.txt` block, pages already
in the index can take months to be removed; a meta tag change takes two to four weeks.

`Crawl-delay` support, JavaScript rendering and how often `robots.txt` is re-read are not
documented on the page checked.

Baidu's FAQ lists a user agent per product: `Baiduspider` (web and mobile search),
`Baiduspider-image` (image search), `Baiduspider-video`, `Baiduspider-news`, `Baiduspider-favo`,
`Baiduspider-cpro` and `Baiduspider-ads`. `Baiduspider-render` is not on that page.

## User agents

Exact strings, one per line (PC search, then mobile search):

```
Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)
Mozilla/5.0 (Linux;u;Android 4.2.2;zh-cn;) AppleWebKit/534.46 (KHTML,like Gecko) Version/5.1 Mobile Safari/10600.6.3 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)
```

Baidu says `Baiduspider/2.0` identifies its crawler, and `Android` with `Mobile` identifies a
mobile crawl. It gives no full string for `Baiduspider-image` or `Baiduspider-render`. According to
Known Agents, `Baiduspider-render` sends:

```
Mozilla/5.0 (compatible; Baiduspider-render/2.0; +http://www.baidu.com/search/spider.html)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Baiduspider
Disallow: /
```

Baidu says this blocks all of Baidu's crawling. Each product's token can get its own rules; Baidu's
example blocks everything but lets image search fetch `/image/`:

```
User-agent: Baiduspider
Disallow: /

User-agent: Baiduspider-image
Allow: /image/
```

`Baiduspider-cpro` (Baidu Union) and `Baiduspider-ads` (business search) do not obey `robots.txt`:
Baidu says they do not index pages, only act on agreements with customers.

## IP ranges and verification

None published. Baidu recommends a reverse DNS lookup followed by a forward lookup: the hostname
must end in `.baidu.com` or `.baidu.jp`, and must resolve back to the same address. Its examples are
`baiduspider-123-125-66-120.crawl.baidu.com` and `BaiduMobaider-119-63-195-254.crawl.baidu.jp`.
No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` parses both strings above as family `Baiduspider`, and the Known Agents
string as `Baiduspider-render`. `src/modules/identity.js` sets the identity `Baidu` for the families
`Baiduspider`, `Baiduspider-render` and `Baiduspider-image` when the unconfirmed hostname ends with
`.baidu.com`. Baidu documents a forward-confirmed check, which the rule does not do, and the
`.baidu.jp` suffix, which the rule does not accept.

## Misc

Baidu says impersonation is common and asks for access logs when a crawler named Baiduspider causes
bandwidth problems.

## Sources

- https://help.baidu.com/question?prod_id=99&class=476&id=2996 (checked 2026-10-15)
- https://knownagents.com/agents/baiduspider-render (checked 2026-10-15)
