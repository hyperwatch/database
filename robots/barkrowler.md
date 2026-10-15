---
name: Barkrowler
operator: Babbar.tech
website: https://babbar.tech
documentation: https://babbar.tech/crawler
category: seo
robots_txt_token: barkrowler
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://www.babbar.tech/barkrowler-ip-ranges.json
  hostnames:
    - babbar.eu
hyperwatch:
  family: Barkrowler
  identity: Babbar
last_checked: 2026-10-15
---

# Barkrowler

## Description

Barkrowler is the crawler of Babbar.tech. It builds and updates a graph of the web. The data and
metrics feed Babbar's online marketing and SEO tools.

## Behavior

Babbar documents:

- It follows `robots.txt`, using the crawler-commons tool set, and honors `Disallow`.
- It waits 5 seconds between two requests to the same host, and 2.5 seconds between requests to
  the same IP for the same domain.
- It follows `Crawl-delay`, applied per host. Servers hosting many domains may still see several
  requests at once.
- It crawls URLs found on public pages, including 301 and 404 pages, and follows links regardless
  of `nofollow`.
- It does not store page content, mainly links and meta information.

JavaScript rendering and how often it reads `robots.txt` are not documented.

## User agents

```
Mozilla/5.0 (compatible; Barkrowler/0.9; +https://babbar.tech/crawler)
```

Babbar's page names the robot and its version (0.9) but does not give the full string.

## Observed HTTP headers

Only header signatures are available (they keep `accept`, `accept-language` and `dnt`), from fewer than 10 distinct signatures seen on 2026-10-15:

- `accept`: `text/html;q=0.95,text/*;q=0.9,*/*;q=0.8`
- `accept-language`: never sent
- `dnt`: never sent

## Blocking with robots.txt

```
User-agent: barkrowler
Disallow: /
```

To slow it down:

```
User-agent: barkrowler
Crawl-Delay: 10
```

## IP ranges and verification

- IP list: https://www.babbar.tech/barkrowler-ip-ranges.json, in the Googlebot JSON format
  (`creationTime` and a `prefixes` array of `ipv4Prefix` objects). When checked it held 2 IPv4
  `/24` ranges and no IPv6, `creationTime` 2024-10-22.
- Reverse DNS: Babbar gives the suffix `babbar.eu`, without example hostnames.

No ASN is documented by Babbar.

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `Barkrowler`. In Hyperwatch `main` (after
5.3.3), `src/modules/identity.js` sets the identity `Babbar` on an unconfirmed hostname ending with
`.babbar.eu` or the published list (`barkrowler-ips.json`). The hostname is not confirmed with a
forward lookup, which Babbar does not mention either: whoever controls an address's reverse DNS can
pass it.

## Misc

Babbar asks site owners to contact it if Barkrowler does not respect a directive, but gives no
address on the crawler page.

## Sources

- https://babbar.tech/crawler (checked 2026-10-15)
- https://www.babbar.tech/barkrowler-ip-ranges.json (checked 2026-10-15)
