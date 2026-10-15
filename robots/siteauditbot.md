---
name: SiteAuditBot
operator: Semrush
website: https://www.semrush.com
documentation: https://www.semrush.com/kb/681-site-audit-troubleshooting
category: seo
robots_txt_token: SiteAuditBot
respects_robots_txt: partial
verification:
  method: both
  ip_list: https://www.semrush.com/kb/681-site-audit-troubleshooting
  hostnames: [".siteaudit.bot.semrush.com"]
hyperwatch:
  family: SiteAuditBot
  identity: Semrush
last_checked: 2026-10-15
---

# SiteAuditBot

## Description

SiteAuditBot is the crawler of Semrush's Site Audit tool. Semrush users run it on a site to
check on-page SEO, technical and usability issues. It crawls when a user starts or schedules an
audit, not continuously.

## Behavior

- It crawls over the standard ports 80 (HTTP) and 443 (HTTPS).
- JavaScript rendering: an option of the audit, available on some paid plans, so the crawler can
  follow links built by JavaScript.
- The audit can start from the website or from its sitemap.
- `robots.txt`: if the site disallows SiteAuditBot, the audit cannot check it. A "Bypass Disallow
  in Robots.txt" option makes the crawler ignore disallow rules. Semrush requires the user to
  verify ownership of the site first.
- `Crawl-delay`, crawl rate and `robots.txt` caching: not documented for SiteAuditBot.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; SiteAuditBot/0.97; +http://www.semrush.com/bot.html)
Mozilla/5.0 (iPhone; CPU iPhone OS 6_0 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) Version/6.0 Mobile/10A5376e Safari/8536.25 (compatible; SiteAuditBot/0.97; +http://www.semrush.com/bot.html)
```

The second string is a mobile variant. Semrush does not publish full user agent strings.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Semrush by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `*/*` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: SiteAuditBot
Disallow: /
```

A user who has verified ownership of the site can make the audit bypass these rules. The other
Semrush tokens are listed in `semrushbot.md`.

## IP ranges and verification

Semrush documents `85.208.98.128/25` as a subnet used by Site Audit only, to allow in firewalls.
It is published as text in a help article, not as a machine-readable list.

Reverse DNS is not documented. In practice, addresses of this subnet have PTR records such as
`<n>.siteaudit.bot.semrush.com` that resolve back to the same address. The range is announced by
AS209366 (Semrush).

## Hyperwatch

`@hyperwatch/useragent` returns the family `SiteAuditBot` for both user agents.
`src/modules/identity.js` sets the identity `Semrush` when the reverse DNS name ends with
`.semrush.com` and is confirmed by a forward lookup, or when the address is in `85.208.98.0/24`.

## Misc

Site Audit is a user-run tool: its traffic follows Semrush customers' audits of a site. SemrushBot
and the other Semrush crawlers are described in `semrushbot.md`.

## Sources

- https://www.semrush.com/kb/681-site-audit-troubleshooting (checked 2026-10-15)
- https://www.semrush.com/bot/ (checked 2026-10-15)
- RADb route object for 85.208.98.0/24, `whois -h whois.radb.net` (checked 2026-10-15)
