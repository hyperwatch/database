---
name: Pinterestbot
operator: Pinterest
website: https://www.pinterest.com
documentation: https://help.pinterest.com/en/business/article/pinterest-crawler
category: social-preview
robots_txt_token: Pinterestbot
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames:
    - .pinterest.com
    - .pinterestcrawler.com
hyperwatch:
  family: Pinterestbot
  identity: Pinterest
last_checked: 2026-10-15
---

# Pinterestbot

## Description

Pinterestbot is Pinterest's crawler. It fetches pages that are saved or linked on Pinterest to show
their content on Pins.

## Behavior

Pinterest says the crawler collects product data (image, title, description, price, availability),
article previews, and the metadata of pages behind Pins to keep it current. It also checks pages to
find and remove broken links and to fight spam. Pinterest says crawled content is not used to train
its Pinterest Canvas image model.

It honors `Crawl-delay` up to 1 second: larger values are treated as 1. It also limits the number
of concurrent requests to a site. JavaScript rendering and `robots.txt` caching are not documented.

## User agents

Exact strings, one per line:

```
Pinterest/0.2 (+https://www.pinterest.com/bot.html)
Mozilla/5.0 (compatible; Pinterestbot/1.0; +https://www.pinterest.com/bot.html)
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2272.96 Mobile Safari/537.36 (compatible; Pinterestbot/1.0; +https://www.pinterest.com/bot.html)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Pinterestbot
Disallow: /
```

Pinterest gives examples with `Allow` and `Disallow` and with `Crawl-delay` (for example
`Crawl-delay: 0.2`). The `robots.txt` file must be on the main domain: subdomains are not
supported.

## IP ranges and verification

Pinterest recommends a forward-confirmed reverse DNS check: the address must resolve to a name
ending with `pinterest.com` or `pinterestcrawler.com`, and that name must resolve back to the same
address.

The page also says that crawling from the US always comes from `54.236.1.0/24` ("54.236.1.001 to
54.236.1.255"), that this range can change without notice, and that crawling from outside the US
has no fixed range. No list file and no ASN are published.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Pinterestbot` for the second and third strings above,
and `Pinterest` for the first one. `src/modules/identity.js` sets the identity `Pinterest` for the
family `Pinterestbot` when the reverse DNS hostname ends with `.pinterest.com`.

Where it falls short of the documentation:

- it reads the unconfirmed hostname, not the forward-confirmed one;
- it does not accept `.pinterestcrawler.com`;
- it does not use the US range;
- the `Pinterest/0.2` user agent (family `Pinterest`) never gets an identity.

## Misc

Pinterest asks site owners to contact it if a client with a valid Pinterest user agent sends
regular traffic but fails the DNS check.

## Sources

- https://help.pinterest.com/en/business/article/pinterest-crawler (checked 2026-10-15)
