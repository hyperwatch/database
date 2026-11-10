---
name: KakaoBot
operator: Kakao
website: https://www.kakaocorp.com
documentation: https://cs.kakao.com/helps_html/1073213012
category: search-engine
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: ip-list
  ip_list: https://cs.kakao.com/helps_html/1073213012
  hostnames: []
hyperwatch:
  family: KakaoBot
  identity: Kakao
last_checked: 2026-11-10
---

# KakaoBot

## Description

KakaoBot is the web document collector run by Kakao, the South Korean company behind KakaoTalk and
Daum. It visits public web pages to build Kakao's search results. Kakao's help page is in Korean
and filed under KakaoTalk search.

## Behavior

Kakao says that when KakaoBot is blocked by a firewall or access control, the site does not appear
in Kakao's search results or stays there with outdated content.

Crawl rate, `Crawl-delay` support, JavaScript rendering and how `robots.txt` is read are not
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; KakaoBot/1.0; +https://cs.kakao.com/helps_html/1073213012)
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; KakaoBot/1.0; +https://cs.kakao.com/helps_html/1073213012) Chrome/131.0.0.0 Safari/537.36
```

Kakao says the version numbers (`1.0`, `131.0.0.0`) may change without notice.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Kakao's page gives no `robots.txt` token and does not say whether KakaoBot obeys
`robots.txt`.

## IP ranges and verification

Kakao lists KakaoBot's addresses on its help page, in HTML, after the sentence "KakaoBot은 다음의
IP를 사용합니다" ("KakaoBot uses the following IPs"), and says the list may change without notice.
On 2026-11-10 it held 23 IPv4 entries: 8 `/27` ranges and 15 single addresses. There is no
machine-readable file and no date. No IPv6, reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `KakaoBot` for both strings. In Hyperwatch `main` (after
5.4.0), `src/modules/identity.js` sets the identity `Kakao` when the address is in the published
list (`kakaobot-ips.json`, 23 entries, the same as the help page on 2026-11-10). The list is read
from the help page by `node scripts/fetch-ips.js` (`listAfter` format: the first list after Kakao's
sentence), so a change in the page's layout can break the refresh.

## Misc

Daum, Kakao's portal, runs its own crawler with its own list: see [Daum](daum.md).

## Sources

- https://cs.kakao.com/helps_html/1073213012 (checked 2026-11-10)
