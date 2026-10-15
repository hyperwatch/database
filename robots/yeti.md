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
last_checked: 2026-10-15
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

No requests from this robot were captured with their headers yet.

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
5.3.3), `src/modules/identity.js` sets the identity `Naver` on an unconfirmed hostname ending with
`.naver.com` or the published list (`naverbot-ips.json`). Naver documents a forward-confirmed check;
the hostname is still not confirmed.

## Misc

Naver also runs `Ads-Naver`, which collects information from advertisers' pages, and `Blueno`,
which fetches link previews for the blog editor and other services.

## Sources

- https://searchadvisor.naver.com/guide/seo-basic-firewall (checked 2026-10-15)
- https://searchadvisor.naver.com/guide/seo-basic-robots (checked 2026-10-15)
- https://searchadvisor.naver.com/doc/naverbot.json (checked 2026-10-15)
- https://help.naver.com/service/5626/contents/8026?lang=ko (checked 2026-10-15)
