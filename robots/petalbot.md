---
name: PetalBot
operator: Huawei (Petal Search)
website: https://petalsearch.com
documentation: https://webmaster.petalsearch.com/site/petalbot
category: search-engine
robots_txt_token: PetalBot
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames:
    - .petalsearch.com
hyperwatch:
  family: PetalBot
  identity: PetalBot
last_checked: 2026-10-15
---

# PetalBot

## Description

PetalBot is the crawler of Petal Search, Huawei's search engine. It fetches PC and mobile sites to
build the index used by Petal Search, and by the Huawei Assistant and AI Search services, which run
on Petal Search.

## Behavior

Huawei says PetalBot adjusts its crawl to server capacity, site quality and how often the site
changes, and takes complaints at petalbot@huawei.com. After a `robots.txt` block, pages already in
the index can take months to be removed.

`Crawl-delay` support, JavaScript rendering and how often `robots.txt` is re-read are not
documented.

## User agents

Exact strings, one per line (PC, then mobile):

```
Mozilla/5.0 (compatible;PetalBot;+https://webmaster.petalsearch.com/site/petalbot)
Mozilla/5.0 (Linux; Android 7.0;) AppleWebKit/537.36 (KHTML, like Gecko) Mobile Safari/537.36 (compatible; PetalBot;+https://webmaster.petalsearch.com/site/petalbot)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: PetalBot
Disallow: /
```

Huawei's example of a partial block:

```
User-agent: PetalBot
Allow: /w/api/
Disallow: /trap/
```

## IP ranges and verification

None published. Huawei recommends a reverse DNS lookup followed by a forward lookup: the hostname
must be in `petalsearch.com`, for example `petalbot-<address with dashes>.petalsearch.com`, and
must resolve back to the same address. The documentation site also has a form that checks whether
an address belongs to PetalBot. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` parses both strings above as family `PetalBot`. `src/modules/identity.js`
sets the identity `PetalBot` when the unconfirmed hostname ends with `.petalsearch.com`. Huawei
documents a forward-confirmed check, which the rule does not do.

## Misc

The documentation page is rendered by JavaScript. Its code still contains text, not shown on the
page, giving the older hostname format `petalbot.*.aspiegel.com`. The user agent parser also maps
`AspiegelBot` to the same pattern as PetalBot.

## Sources

- https://webmaster.petalsearch.com/site/petalbot (checked 2026-10-15, text read from the page's
  JavaScript bundle)
