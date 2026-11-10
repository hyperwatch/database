---
name: Yeti
operator: Naver
website: https://www.naver.com
documentation: https://searchadvisor.naver.com/guide/seo-basic-firewall
category: search-engine
robots_txt_token: Yeti
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://searchadvisor.naver.com/doc/naverbot.json
  hostnames:
    - .naver.com
hyperwatch:
  family: Yeti
  identity: Naver
last_checked: 2026-11-10
---

# Yeti

## Description

Yeti is the crawler of Naver, the South Korean search engine. It collects web documents for Naver's
general search service.

## Behavior

Naver says Yeti obeys `robots.txt`, and treats a site without one as fully open. How it reads
`robots.txt` depends on the response:

- 2xx: the rules are used. A `robots.txt` returned as HTML may be read as "allow all".
- 3xx: up to 5 redirects are followed, then the file is treated as "allow all". HTML and JavaScript
  redirects are not followed.
- 4xx: "allow all".
- 5xx: "disallow all", though rules fetched earlier may be used for a while.

A `robots.txt` applies to one host, protocol and port only. Yeti may fetch favicons, JavaScript and
CSS files used by an allowed page even when `robots.txt` blocks them. `Crawl-delay` support is not
documented on the pages checked.

## User agents

Exact strings, one per line (`W.X.Y.Z` is a browser version):

```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko; compatible; Yeti/1.1; +https://naver.me/spd) Chrome/W.X.Y.Z Safari/537.36
Mozilla/5.0 (compatible; Yeti/1.1; +https://naver.me/spd)
```

Naver says version details may change without notice.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-11-10, pages, verified as Naver by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8` (57%), `*/*` (43%) |
| `accept-language` | `ko-KR,ko;q=0.8,en-US;q=0.6,en;q=0.4` (100%) |
| `sec-fetch-dest` | `document` (57%), `empty` (43%) |
| `sec-fetch-mode` | `navigate` (57%), `cors` (43%) |
| `sec-fetch-site` | `none` (57%), `same-origin` (43%) |
| `signature` | `(present)` (100%) |
| `signature-agent` | `sig1="https://bot.naver.com"` (100%) |
| `signature-input` | `(present)` (100%) |
| `sunny-proxy-server-address` | `(present)` (43%) |

## Blocking with robots.txt

```
User-agent: Yeti
Disallow: /
```

Naver says robots with special purposes, such as those collecting advertiser information or
building link previews, may not follow `robots.txt` fully, and neither may robots covered by an
agreement with the site.

## IP ranges and verification

Naver documents two checks:

- Reverse DNS: the hostname must end in `.naver.com` and resolve back to the same address. Its
  example is `crawl.125-209-235-169.web.naver.com`.
- IP list: https://searchadvisor.naver.com/doc/naverbot.json, which may change without notice. The
  file is JSON with a `creationTime` field and a `prefixes` array of objects with an `ipv4Prefix`
  key. On 2026-10-15 it held 36 IPv4 prefixes and was dated 2024-07-12.

No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` parses both strings above as family `Yeti`. In Hyperwatch `main` (after
5.4.0), `src/modules/identity.js` sets the identity `Naver` on a forward-confirmed hostname matching
`crawl.*.web.naver.com`, the published list (`naverbot-ips.json`) or a verified signature of
`https://bot.naver.com` (needs the `webbotauth` module, off by default). Naver signs with the
dictionary form of `Signature-Agent` (`sig1="https://bot.naver.com"`), covering `@method` and
`@path` too. A "hostname only" fallback sets `Naver` on the same forward-confirmed names whatever
the user agent. The pattern follows Naver's example name, narrower than the documented `.naver.com`
suffix.

## Misc

Naver also runs `Ads-Naver`, which collects information from advertisers' pages, and `Blueno`,
which fetches link previews for the blog editor and other services.

## Sources

- https://searchadvisor.naver.com/guide/seo-basic-firewall (checked 2026-10-15)
- https://searchadvisor.naver.com/guide/seo-basic-robots (checked 2026-10-15)
- https://searchadvisor.naver.com/doc/naverbot.json (checked 2026-10-15)
- https://help.naver.com/service/5626/contents/8026?lang=ko (checked 2026-10-15)
