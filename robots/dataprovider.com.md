---
name: Dataprovider.com
operator: Dataprovider.com
website: https://www.dataprovider.com
documentation: https://www.dataprovider.com/crawler/
category: marketing
robots_txt_token: dataprovider
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames:
    - dataproviderbot.com
hyperwatch:
  family: Dataprovider.com
  identity: Dataprovider.com
last_checked: 2026-11-19
---

# Dataprovider.com

## Description

Dataprovider.com sells structured data about websites and the companies behind them (technology,
business information, classifications, risk), used for asset management, brand protection,
business information and market research. Its in-house crawler indexes, each month, what it
describes as the entire internet of over 400 million domains.

## Behavior

Dataprovider.com says the crawler "works very efficiently" to avoid inconvenience and save
bandwidth, that it always looks for `robots.txt` before indexing a site, and that it follows the
robots `META` tag (`noindex`, `nofollow`). Crawl rate, `Crawl-delay` support, JavaScript rendering
and how long `robots.txt` is cached are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; Dataprovider.com)
```

This matches the string on Dataprovider.com's crawler page.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: dataprovider
Disallow: /
```

Dataprovider.com says the crawler obeys `dataprovider` (to disallow only Dataprovider.com) or `*`.
A site can also opt out through Dataprovider.com's contact page.

## IP ranges and verification

None published. Dataprovider.com says to identify the crawler by reverse DNS: a name containing
`dataproviderbot.com`. It does not say to confirm the name with a forward lookup. No ASN is
documented, and no Web Bot Auth key directory.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1, which Hyperwatch 5.7.0 depends on, returns the family
`Dataprovider.com`. `src/modules/identity.js` has no rule for that family. In Hyperwatch 5.7.0, the
"hostname only" fallback sets the identity `Dataprovider.com` on a forward-confirmed hostname
matching `crawl-*.dataproviderbot.com`, whatever the user agent.

Where it falls short: the `crawl-*` prefix is narrower than the documentation, which only names
`dataproviderbot.com`, so a confirmed name under that domain that does not start with `crawl-`
gets no identity.

## Misc

Nothing else documented.

## Sources

- https://www.dataprovider.com/crawler/ (checked 2026-11-19)
