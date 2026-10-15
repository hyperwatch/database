---
name: Claude-SearchBot
operator: Anthropic
website: https://www.anthropic.com
documentation: https://support.claude.com/en/articles/8896518-does-anthropic-crawl-the-web
category: ai-search
robots_txt_token: Claude-SearchBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://claude.com/crawling/bots.json
  hostnames: []
hyperwatch:
  family: Claude-SearchBot
  identity: Claude
last_checked: 2026-10-15
---

# Claude-SearchBot

## Description

Claude-SearchBot is Anthropic's crawler for search. Anthropic says it navigates the web to improve
the quality of search results for Claude users. Blocking it prevents Anthropic from indexing a
site's content for search, which may reduce the site's visibility in Claude's answers.

## Behavior

- `robots.txt`: Anthropic says its bots honor standard `robots.txt` directives.
- `Crawl-delay`: supported by Anthropic's bots (the help article's example uses ClaudeBot).
- Crawl rate, JavaScript rendering and `robots.txt` caching: not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Claude-SearchBot/1.0; +claudebot@anthropic.com)
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Claude-SearchBot/1.0; +searchbot@anthropic.com)
```

Anthropic does not publish full user agent strings, only the token. The contact address in the
string varies.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Claude-SearchBot
Disallow: /
```

This token is independent of `ClaudeBot` (training) and `Claude-User` (user fetches).

## IP ranges and verification

Anthropic publishes one list for all its crawlers: https://claude.com/crawling/bots.json (JSON,
`prefixes` array of `ipv4Prefix` objects, 38 IPv4 prefixes on 2026-10-15). See `claudebot.md`. No
reverse DNS hostnames are published.


## Hyperwatch

`@hyperwatch/useragent` returns the family `Claude-SearchBot`. `src/modules/identity.js` sets the
identity `Claude` when the address is in `src/data/claude-bot-ips.json`, Hyperwatch's copy of
Anthropic's list.

## Misc

See `claudebot.md` and `claude-user.md` for Anthropic's other robots.

## Sources

- https://support.claude.com/en/articles/8896518-does-anthropic-crawl-the-web (checked 2026-10-15)
- https://claude.com/crawling/bots.json (checked 2026-10-15)
