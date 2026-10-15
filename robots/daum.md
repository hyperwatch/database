---
name: Daum
operator: Kakao (Daum)
website: https://www.daum.net
documentation: https://cs.daum.net/faq/service/15/category/4118/detail/28961
category: search-engine
robots_txt_token: Daum
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://webmaster.daum.net/crawler/daumbot.json
  hostnames: []
hyperwatch:
  family: Daum
  identity: Daum
last_checked: 2026-10-15
---

# Daum

## Description

The Daum crawler collects web documents for Daum's web document search. Daum is the South Korean
portal run by Kakao.

## Behavior

Daum says the crawler follows links in documents to find new ones, obeys the rules at
http://www.robotstxt.org/, and picks up changes to a site's rules quickly. Some partner sites give
it specific rules, which it follows. Collected documents are used only for web document search.

Crawl rate, `Crawl-delay` support, JavaScript rendering and how often `robots.txt` is re-read are
not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; Daum/4.1; +https://cs.daum.net/faq/service/15/category/4118/detail/28966)
```

Daum says `Daum/4.1` identifies the crawler, and that the format may change without notice. The user
agent parser also knows the name `Daumoa`, which Daum's pages do not mention.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Daum
Disallow: /
```

The token is `Daum`, case-insensitive. Daum also documents the `robots` meta tag
(`noindex, nofollow`) to exclude a page.

## IP ranges and verification

Daum publishes an address list shared by the crawler and Daum Preview at
https://webmaster.daum.net/crawler/daumbot.json, and says to refresh it regularly. The file is JSON
with a `creationTime` field and a `prefixes` array of objects with an `ipv4Prefix` key. On
2026-10-15 it held 52 IPv4 prefixes and was dated 2026-08-20.

No reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `Daum`. In Hyperwatch `main` (after
5.3.3), `src/modules/identity.js` sets the identity `Daum` when the address is in the published list
`src/data/daumbot-ips.json`. That file is Daum's daumbot.json copied by hand (52 prefixes, the same
count as on 2026-10-15): Daum's server does not send its intermediate certificate, so Hyperwatch's
fetch script cannot download it. Because the copy is manual, it is not refreshed when Daum updates
the list. There is no rule for the family `Daumoa`.

## Misc

Daum also runs Daum Preview (`Daum-Preview/1.0`), which fetches link previews for Daum services. It
fetches one page, follows redirects, does not run JavaScript, and its data is not used for search.

## Sources

- https://cs.daum.net/faq/service/15/category/4118/detail/28961 (checked 2026-10-15)
- https://cs.daum.net/faq/service/15/category/4118/detail/28966 (checked 2026-10-15)
- https://cs.daum.net/faq/service/15/category/4118/detail/36354 (checked 2026-10-15)
- https://webmaster.daum.net/crawler/daumbot.json (checked 2026-10-15)
