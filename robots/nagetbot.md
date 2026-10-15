---
name: NagetBot
operator: Naget
website: https://naget.com
documentation: https://naget.com/bot
category: ai-search
robots_txt_token: NagetBot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: NagetBot
  identity: null
last_checked: 2026-10-15
---

# NagetBot

## Description

NagetBot is the crawler behind Naget, an AI search system. It visits public pages to add them to
the index Naget searches, and Naget shows those pages as linked sources. Naget presents itself as a
technology transfer of the Center for Intelligent Information Retrieval (CIIR) at the University of
Massachusetts Amherst.

## Behavior

Naget documents:

- It spaces out requests per site. After consecutive errors it doubles the wait, up to 10 seconds
  between requests.
- It follows `Crawl-delay` as the minimum number of seconds between requests. A value of one second
  or more also limits it to one request at a time.
- It refreshes `robots.txt` every 24 hours, so changes can take a day to apply. With no
  `robots.txt`, every page is treated as allowed.
- It does not run JavaScript, fill in forms or sign in.
- It fetches HTML pages only, reads at most 5 MB per page and follows up to five redirects.

## User agents

```
Mozilla/5.0 (compatible; NagetBot/1.0; +https://naget.ai/bot)
```

This matches the string documented by Naget. `https://naget.ai/bot` redirects to
`https://naget.com/bot`.

## Observed HTTP headers

Only header signatures are available (they keep `accept`, `accept-language` and `dnt`), from fewer than 10 distinct signatures seen on 2026-10-15:

- `accept`: `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8`
- `accept-language`: `en-US,en;q=0.9`
- `dnt`: never sent

## Blocking with robots.txt

```
User-agent: NagetBot
Disallow: /
```

NagetBot follows the group naming `NagetBot`, or the `*` group if there is none. To slow it down:

```
User-agent: NagetBot
Crawl-delay: 10
```

## IP ranges and verification

None published. No reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS47007 Colocation America Corporation: `67.227.120.0/24`, `216.74.75.0/24`, `216.10.0.0/24`, `185.207.96.0/24`
- AS13886 Cloud South: `104.249.4.0/24`, `104.233.53.0/24`, `104.233.50.0/24`, `104.249.1.0/24`, `104.239.115.0/24`
- AS16591 Google Fiber Inc.: `136.47.217.0/24`

Reverse DNS hostnames:

- `*.rdns.ColocationAmerica.com` (not forward-confirmed)
- `*.googlefiber.net` (not forward-confirmed)
- `*.colocationamerica.com` (not forward-confirmed)

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `NagetBot`. `src/modules/identity.js` has no
rule for it, so it gets no identity.

## Misc

Naget's contact address is info@naget.com. It asks for the domain and, if possible, a few lines
of access log when reporting a problem.

## Sources

- https://naget.ai/bot (redirects to https://naget.com/bot) (checked 2026-10-15)
- https://naget.com/bot (checked 2026-10-15)
- https://naget.com/about (checked 2026-10-15)
