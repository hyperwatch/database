---
name: HaloBot
operator: HaloScan
website: https://www.haloscan.com
documentation: https://www.haloscan.com/en/crawler-haloscan
category: seo
robots_txt_token: halobot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://www.haloscan.com/en/crawler-haloscan
  hostnames: []
hyperwatch:
  family: HaloBot
  identity: null
last_checked: 2026-10-15
---

# HaloBot

## Description

HaloBot is the crawler of HaloScan, an SEO tool. The user agent has no URL, but HaloScan documents
the exact string on its own crawler page. It collects links, redirects, status codes, language and
technical tags from public pages to build HaloScan's backlink and domain database. HaloScan says it
does not aim to store the raw content of pages.

## Behavior

- It visits URLs found on public pages, URLs of domains already known to HaloScan, redirect
  targets, and pages it re-checks for changes.
- It re-visits URLs that returned redirects, 404/410, 5xx errors or timeouts. HaloScan says the
  re-check frequency depends on several signals and may decrease when a status does not change.
- It may follow `nofollow` links.
- `Crawl-delay` is supported.
- No crawl rate is documented. JavaScript rendering is not documented. How often `robots.txt` is
  re-read is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; HaloBot/1.0)
```

This matches the string documented by HaloScan.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: halobot
Disallow: /
```

HaloScan says the crawler "reads and applies the compatible directives present in the robots.txt
file of each visited host", including `Crawl-delay`.

## IP ranges and verification

HaloScan lists 12 "official IP addresses" as an HTML table on its crawler page (single IPv4
addresses, no CIDR ranges, no IPv6, no machine-readable file). No reverse DNS hostname or ASN is
documented. HaloScan asks people to report "a suspicious IP address using our name".

## Hyperwatch

`@hyperwatch/useragent` returns the family `HaloBot`. `src/modules/identity.js` has no rule for it,
so it gets no identity.

## Misc

- Not to be confused with `HaloAgentsAI-Crawler`, a different robot from Halo Agents.
- The crawler page was last updated on 11/07/2026, according to the page itself.

## Sources

- https://www.haloscan.com/en/crawler-haloscan (checked 2026-10-15)
- https://knownagents.com/agents/halobot (checked 2026-10-15)
- https://crawlconsole.com/web-crawlers/halobot (checked 2026-10-15)
