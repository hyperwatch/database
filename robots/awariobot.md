---
name: AwarioBot
operator: Awario
website: https://awario.com
documentation: https://awario.com/bots.html
category: marketing
robots_txt_token: AwarioSmartBot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: AwarioBot
  identity: WebMeUp
last_checked: 2026-10-15
---

# AwarioBot

## Description

Awario is a social listening and brand monitoring service. Its crawlers, AwarioSmartBot and
AwarioRssBot, collect public web pages so that Awario customers can find mentions of their brand
online. The user agent `AwarioBot/1.0` is listed by Awario as one of the forms these crawlers use.

## Behavior

- Crawl rate: at most one request every 3 seconds, or slower if `robots.txt` sets a longer
  `Crawl-delay`.
- `Crawl-delay`: supported.
- A page is fetched when its content has never been collected or needs to be refreshed. Awario
  says there are no recurring requests to the same page.
- Awario states that the crawlers only collect publicly available information.
- JavaScript rendering and `robots.txt` caching: not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; AwarioBot/1.0; +https://awario.com/bots.html)
```

Other documented strings:

```
AwarioSmartBot/1.0 (+https://awario.com/bots.html; bots@awario.com)
AwarioRssBot/1.0 (+https://awario.com/bots.html; bots@awario.com)
```

## Observed HTTP headers

Based on hundreds of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as WebMeUp by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

Awario documents two tokens:

```
User-agent: AwarioRssBot
User-agent: AwarioSmartBot
Disallow: /
```

To slow the crawlers down:

```
User-agent: AwarioRssBot
User-agent: AwarioSmartBot
Crawl-delay: 10
```

Awario does not document `AwarioBot` as a `robots.txt` token, although it lists the
`AwarioBot/1.0` user agent under the same crawlers.

## IP ranges and verification

None published. Awario asks site owners not to identify the crawlers by IP address, because it
does not use consecutive IP blocks. No reverse DNS hostnames are documented.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS24940 Hetzner Online GmbH: `65.21.113.0/24`

Reverse DNS hostnames:

- `*.webmeup.com` (forward-confirmed)

## Hyperwatch

`@hyperwatch/useragent` returns the family `AwarioBot`. `src/modules/identity.js` sets the
identity `WebMeUp` for this family when the reverse DNS name ends with `.webmeup.com` (the same
rule as BLEXBot). The hostname is not confirmed by a forward lookup in this rule, and Awario does
not document it. Without such a hostname, the identity is null.

## Misc

Problems with the crawlers can be reported to bots@awario.com.

## Sources

- https://awario.com/bots.html (checked 2026-10-15)
