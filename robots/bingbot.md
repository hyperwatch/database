---
name: bingbot
operator: Microsoft
website: https://www.bing.com
documentation: https://www.bing.com/webmasters/help/which-crawlers-does-bing-use-8c184ec0
category: search-engine
robots_txt_token: bingbot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://www.bing.com/toolbox/bingbot.json
  hostnames:
    - search.msn.com
hyperwatch:
  family: BingBot
  identity: Bing
last_checked: 2026-10-15
---

# bingbot

## Description

bingbot is the main crawler of Microsoft Bing. It fetches pages to build the Bing search index,
which also serves other products that rely on Bing results.

## Behavior

- Since October 2019 bingbot renders pages with Microsoft Edge (Chromium) and runs JavaScript.
  Microsoft calls it "evergreen": the rendering engine follows recent stable Edge versions, and the
  user agent includes a Chrome version token that changes over time.
- Bing supports `Crawl-delay`. Bing describes the value as a relative slow-down from its default
  crawl rate, accepts only positive whole numbers, and advises against values above 10. Crawl rate
  can also be set in Bing Webmaster Tools (Crawl Control).
- How often `robots.txt` is re-read is not documented on the pages checked.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm)
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm) Chrome/116.0.1938.76 Safari/537.36
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm) Chrome/136.0.0.0 Safari/537.36 AppleWebKit/537.36 (KHTML, like Gecko; compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm) Chrome/116.0.1938.76 Safari/537.36
```

The third string repeats the bingbot part twice, as received. The older form
`Mozilla/5.0 (compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm)` is also widely
documented. `http://www.bing.com/bingbot.htm` redirects to the Bing crawlers help page.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Bing by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `*/*` (100%) |
| `from` | `bingbot(at)microsoft.com` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: bingbot
Disallow: /
```

`Crawl-delay` is supported (see Behavior). Other Microsoft crawlers have their own tokens, for
example `adidxbot` (Bing Ads) and `MicrosoftPreview` (page previews).

## IP ranges and verification

Microsoft publishes bingbot's addresses at https://www.bing.com/toolbox/bingbot.json. The format
is an object with `creationTime` and a `prefixes` array of `{"ipv4Prefix": ...}` objects. On the
check date it held 28 IPv4 prefixes and no IPv6, with `creationTime` 2024-01-03.

Microsoft's documented check is reverse DNS: the address must resolve to a name ending in
`search.msn.com`, and a forward lookup of that name must return the same address. Bing Webmaster
Tools also has a "Verify Bingbot" tool (https://www.bing.com/toolbox/verify-bingbot).


## Hyperwatch

`@hyperwatch/useragent` returns the family `BingBot`. In Hyperwatch `main` (after 5.3.3),
`src/modules/identity.js` sets the identity `Bing` for the families `BingBot` and `BingPreview` on
an unconfirmed hostname ending with `.search.msn.com` or the published list (`bingbot-ips.json`). It
also sets `Bing` for any request whose unconfirmed hostname ends with `.search.msn.com` when no
other rule matched. Bing documents a forward lookup back to the same address; the hostname is still
not confirmed.

## Misc

- Other Microsoft crawler tokens include `adidxbot` (Bing Ads), `BingPreview` (older page
  snapshots) and `MicrosoftPreview` (page previews for Microsoft products). `MSNBot` was the
  previous crawler name. `@hyperwatch/useragent` returns the family `adidxbot` for AdIdxBot.
- Microsoft's crawler help page is rendered with JavaScript and could not be read directly; the
  tokens above come from secondary sources.

## Sources

- https://www.bing.com/webmasters/help/which-crawlers-does-bing-use-8c184ec0 (checked 2026-10-15, content not readable without JavaScript)
- https://www.bing.com/toolbox/bingbot.json (checked 2026-10-15)
- https://www.bing.com/toolbox/verify-bingbot (checked 2026-10-15)
- https://blogs.bing.com/webmaster/2012/08/31/how-to-verify-that-bingbot-is-bingbot (checked 2026-10-15)
- https://blogs.bing.com/webmaster/2009/08/10/crawl-delay-and-the-bing-crawler-msnbot (checked 2026-10-15)
- https://blogs.bing.com/webmaster/october-2019/The-new-evergreen-Bingbot-simplifying-SEO-by-leveraging-Microsoft-Edge (checked 2026-10-15)
- https://en.wikipedia.org/wiki/Bingbot (checked 2026-10-15)
- https://www.xseek.io/docs/bing-ai-user-agents (checked 2026-10-15)
- https://knownagents.com/agents/adidxbot (checked 2026-10-15)
