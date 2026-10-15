---
name: MBCrawler
operator: Monitor Backlinks
website: https://monitorbacklinks.com
documentation: https://monitorbacklinks.com/robot
category: seo
robots_txt_token: MBCrawler
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: MBCrawler
  identity: Monitor Backlinks
last_checked: 2026-10-15
---

# MBCrawler

## Description

MBCrawler is the crawler of Monitor Backlinks, a tool that tracks the backlinks of its users'
sites. It checks the pages where those links are, to report their status.

The URL in its user agent, https://monitorbacklinks.com/robot, redirected on 2026-10-15 to
https://www.seoptimer.com/monitor-backlinks/, which answered with a Cloudflare challenge page and
could not be read. Everything below comes from the Internet Archive's copies of two Monitor
Backlinks help articles captured on 2019-07-17.

## Behavior

According to those articles, Monitor Backlinks does not crawl sites that block its robot in
`robots.txt`, and says it crawls "responsibly". Crawl rate, `Crawl-delay`, JavaScript rendering
and how often `robots.txt` is read are not documented.

## User agents

Exact strings, one per line:

```
MBCrawler/1.0 (https://monitorbacklinks.com/robot)
```

The archived help article gives the user agent as `MBCrawler/1.0`. The full string comes from
Known Agents (formerly Dark Visitors), a third-party bot directory: no readable operator page gives it.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: MBCrawler
Disallow: /
```

The archived article suggests blocking the user agent `MBCrawler/1.0`, or blocking all crawlers in
`robots.txt`. It gives no example with the token.

## IP ranges and verification

None published in the archived articles. The live robot page could not be read.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `MBCrawler`. Hyperwatch sets the
identity `Monitor Backlinks` when the hostname ends with `.compute-1.amazonaws.com`. This is a
cloud hostname: any customer of Amazon EC2 in that region passes, and it is not confirmed by a
forward lookup. The operator documents no hostname or range.

## Misc

The redirect suggests Monitor Backlinks is now part of SEOptimer. According to Known Agents, the
operator is SEOptimer. This could not be confirmed on a readable operator page.

## Sources

- https://monitorbacklinks.com/robot (checked 2026-10-15: redirects to https://www.seoptimer.com/monitor-backlinks/, behind a Cloudflare challenge)
- https://web.archive.org/web/20190717043834/https://help.monitorbacklinks.com/en/articles/2701751-i-want-to-block-or-whitelist-your-crawler-how-do-i-do-that (checked 2026-10-15)
- https://web.archive.org/web/20190717045913/https://help.monitorbacklinks.com/en/articles/915491-how-do-you-get-around-collecting-links-on-websites-that-want-to-block-you-crawling-their-site (checked 2026-10-15)
- https://knownagents.com/agents/mbcrawler (checked 2026-10-15)
