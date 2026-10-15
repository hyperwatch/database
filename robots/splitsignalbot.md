---
name: SplitSignalBot
operator: Semrush
website: https://www.semrush.com
documentation: https://www.semrush.com/bot/
category: seo
robots_txt_token: SplitSignalBot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: SplitSignalBot
  identity: Semrush
last_checked: 2026-10-15
---

# SplitSignalBot

## Description

SplitSignalBot is a Semrush crawler used by "the SplitSignal tool to create SEO A/B tests on your
website", according to Semrush's bot page. SplitSignal is Semrush's SEO split-testing tool.

## Behavior

Not documented beyond its purpose. Crawl rate, `Crawl-delay` support, JavaScript rendering and
`robots.txt` caching are not documented for SplitSignalBot. The crawl-delay and caching rules on
Semrush's page are given for SemrushBot only.

## User agents

Not published. Semrush gives only the `robots.txt` token `SplitSignalBot`, and no full string was
found in other bot lists.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SplitSignalBot
Disallow: /
```

Semrush gives this record "to block SplitSignalBot from crawling your site for SplitSignal tool".
The other Semrush tokens must be blocked separately: see `semrushbot.md`.

## IP ranges and verification

None published for SplitSignalBot. Semrush's bot page documents no IP list or reverse DNS method
for it.

## Hyperwatch

`@hyperwatch/useragent` returns the family `SplitSignalBot` for the bare token and for a string in
the `Mozilla/5.0 (compatible; <token>; +http://www.semrush.com/bot.html)` form used by SemrushBot
(the real string is not published). `src/modules/identity.js` sets the identity `Semrush` when the
forward-confirmed hostname ends with `.semrush.com`, or when the address is in the inline range
`85.208.98.0/24`. Semrush documents neither for SplitSignalBot: the hostname suffix is not
documented for any Semrush crawler, and the only documented range, `85.208.98.128/25`, is for
Site Audit.

## Misc

On 2026-10-15, `https://www.splitsignal.com/` served only a script redirecting to `/lander`, and
Semrush's knowledge base article on SplitSignal (`/kb/1145-splitsignal`) redirected to
`https://enterprise.semrush.com/`. Whether the tool is still offered separately is not documented.

## Sources

- https://www.semrush.com/bot/ (checked 2026-10-15)
- https://www.splitsignal.com/ (checked 2026-10-15)
- https://www.semrush.com/kb/1145-splitsignal (redirects, checked 2026-10-15)
