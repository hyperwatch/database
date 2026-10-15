---
name: ClaudeBot
operator: Anthropic
website: https://www.anthropic.com
documentation: https://support.claude.com/en/articles/8896518-does-anthropic-crawl-the-web
category: ai-training
robots_txt_token: ClaudeBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://claude.com/crawling/bots.json
  hostnames: []
hyperwatch:
  family: ClaudeBot
  identity: Claude
last_checked: 2026-10-15
---

# ClaudeBot

## Description

ClaudeBot is Anthropic's web crawler for model training. Anthropic says it collects web content
that could contribute to the training of its generative AI models. Blocking it signals that a
site's future content should be excluded from training datasets.

## Behavior

- `robots.txt`: Anthropic says its bots honor standard `robots.txt` directives.
- `Crawl-delay`: supported (a non-standard extension).
- Anthropic says its bots do not try to get around CAPTCHAs.
- Each subdomain needs its own `robots.txt`.
- Crawl rate, JavaScript rendering and `robots.txt` caching: not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; ClaudeBot/1.0; +claudebot@anthropic.com)
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36; ClaudeBot/1.0; +claudebot@anthropic.com)
```

Anthropic does not publish full user agent strings, only the token. The second string, with a
desktop Chrome prefix, is not documented.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: ClaudeBot
Disallow: /
```

To slow it down:

```
User-agent: ClaudeBot
Crawl-delay: 1
```

`ClaudeBot`, `Claude-User` and `Claude-SearchBot` are separate tokens. Blocking ClaudeBot does not
block the other two. Anthropic notes that blocking its IP addresses may not work as an opt-out,
because the bots then cannot read `robots.txt`.

## IP ranges and verification

Anthropic publishes one list for all its crawlers: https://claude.com/crawling/bots.json. It is a
JSON object with `creationTime` and `prefixes`, an array of objects with an `ipv4Prefix` key in
CIDR notation. On 2026-10-15 it held 38 IPv4 prefixes (creation time 2026-10-07), no IPv6. A
request from an address in this list comes from Anthropic.

No reverse DNS hostnames are published. The crawlers run on shared cloud infrastructure.

## Hyperwatch

`@hyperwatch/useragent` returns the family `ClaudeBot` for both strings.
`src/modules/identity.js` sets the identity `Claude` for the families `ClaudeBot`, `Claude-User`,
`Claude-SearchBot`, `Claude-Web` and `anthropic-ai` when the address is in
`src/data/claude-bot-ips.json`, a copy of Anthropic's list refreshed by
`scripts/fetch-anthropic-ips.js`. On 2026-10-15 the copy had 28 entries and the published list 38.

## Misc

Anthropic's other robots are Claude-User (fetches on behalf of Claude users) and Claude-SearchBot
(search indexing). `anthropic-ai` and `Claude-Web` are older tokens, no longer described in the
help article. Bot problems can be reported to claudebot@anthropic.com, from an address on the
domain concerned.

## Sources

- https://support.claude.com/en/articles/8896518-does-anthropic-crawl-the-web (checked 2026-10-15)
- https://claude.com/crawling/bots.json (checked 2026-10-15)
