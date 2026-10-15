---
name: SemrushBot
operator: Semrush
website: https://www.semrush.com
documentation: https://www.semrush.com/bot/
category: seo
robots_txt_token: SemrushBot
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames: [".bot.semrush.com"]
hyperwatch:
  family: SemrushBot
  identity: Semrush
last_checked: 2026-10-15
---

# SemrushBot

## Description

SemrushBot is the main crawler of Semrush, an SEO software company. It builds the link index used
by Backlink Analytics and feeds many other Semrush tools. Semrush runs several other crawlers with
their own `robots.txt` tokens. Some of them use a `SemrushBot-` prefix: SemrushBot-BA for the
Backlink Audit tool and SemrushBot-SI for the On Page SEO Checker and similar tools. They are
listed in this file. SiteAuditBot has its own file.

## Behavior

SemrushBot starts from a list of URLs, saves the links found on each page and revisits this
"crawl frontier" according to Semrush's policies.

- `Crawl-delay`: supported by SemrushBot, up to 10 seconds. Higher values are treated as 10.
  Without `Crawl-delay`, it adjusts its request rate to the current server load.
- `robots.txt` caching: changes can take up to one hour or 100 requests to be noticed.
- `robots.txt` status codes: a 4xx answer means no restrictions, a 5xx answer blocks the whole
  site. The file must return HTTP 200 to be used.
- JavaScript rendering: not documented.
- The page does not document crawl rate or `Crawl-delay` for the other Semrush crawlers.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; SemrushBot; +http://www.semrush.com/bot.html)
Mozilla/5.0 (compatible; SemrushBot/7~bl; +http://www.semrush.com/bot.html)
Mozilla/5.0 (compatible; SemrushBot-BA; +http://www.semrush.com/bot.html)
Mozilla/5.0 (compatible; SemrushBot-SI/0.97; +http://www.semrush.com/bot.html)
SemrushBot-EO
```

Semrush does not publish full user agent strings, only `robots.txt` tokens. The `7~bl` suffix
is not documented. `SemrushBot-EO` is not listed on Semrush's bot page.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: SemrushBot
Disallow: /
```

Each Semrush crawler has its own token and must be blocked separately:

| Token | Used for |
|---|---|
| `SemrushBot` | Backlink Analytics link index and many other tools |
| `SemrushBot-BA` | Backlink Audit |
| `SemrushBot-SI` | On Page SEO Checker and similar tools |
| `SemrushBot-SWA` | SEO Writing Assistant (checks that URLs are accessible) |
| `SemrushBot-OCOB` | Content Toolkit |
| `SemrushBot-FT` | Plagiarism Checker and similar tools |
| `SemrushBot-ESI` | Semrush Enterprise Site Intelligence |
| `SiteAuditBot` | Site Audit (see `siteauditbot.md`) |
| `SplitSignalBot` | SplitSignal SEO A/B tests |
| `RyteBot` | Tools provided by Ryte.com |

To slow SemrushBot down:

```
User-agent: SemrushBot
Crawl-delay: 10
```

`SemrushBot-EO` has no documented token.

## IP ranges and verification

None published. Semrush asks site owners not to block SemrushBot by IP address, because it does
not use consecutive IP blocks. No reverse DNS method is documented.

In practice, many Semrush crawler addresses have PTR records under `bot.semrush.com` (for example
`<n>.bl.bot.semrush.com`) that resolve back to the same address. Some addresses have the generic
PTR `bot.semrush.com`, which does not resolve back to them. The range `85.208.98.0/24` is
announced by AS209366 (Semrush). This is not documented by Semrush.

## Hyperwatch

`@hyperwatch/useragent` returns the family `SemrushBot` for the plain, `/7~bl`, `-BA` and `-SI`
user agents. `SemrushBot-EO` parses as its own family, `SemrushBot-EO`.

`src/modules/identity.js` sets the identity `Semrush` for the families `SemrushBot`,
`SemrushBot-SWA`, `SemrushBot-OCOB`, `SemrushBot-FT`, `SemrushBot-ESI`, `SiteAuditBot`,
`SplitSignalBot` and `RyteBot` when the reverse DNS name ends with `.semrush.com` and is confirmed
by a forward lookup, or when the address is in `85.208.98.0/24`. Other families, such as
`SemrushBot-EO`, get the identity `Semrush` from a confirmed hostname ending with `.semrush.com`
only.

## Misc

Questions about the crawler go to bot@semrush.com.

## Sources

- https://www.semrush.com/bot/ (checked 2026-10-15)
- https://www.semrush.com/kb/681-site-audit-troubleshooting (checked 2026-10-15)
- RADb route objects for 85.208.96.0/22 and 85.208.98.0/24, `whois -h whois.radb.net` (checked 2026-10-15)
