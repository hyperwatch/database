---
name: Claude-User
operator: Anthropic
website: https://www.anthropic.com
documentation: https://support.claude.com/en/articles/8896518-does-anthropic-crawl-the-web
category: ai-assistant
robots_txt_token: Claude-User
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://claude.com/crawling/bots.json
  hostnames: []
hyperwatch:
  family: Claude-User
  identity: Claude
last_checked: 2026-10-15
---

# Claude-User

## Description

Claude-User fetches web pages when a person asks Claude a question that needs them. It is not an
automatic crawler: each fetch follows a user's request. Anthropic says disabling it prevents Claude
from retrieving a site's content in response to a user query.

The same name appears in the user agent of Claude Code, Anthropic's command-line coding tool, when
it fetches a URL (`Claude-User (claude-code/<version>; ...)`).

## Behavior

- `robots.txt`: Anthropic lists Claude-User among the bots site owners can disable with
  `robots.txt`, and says its bots honor standard `robots.txt` directives.
- Crawl rate, `Crawl-delay`, JavaScript rendering and `robots.txt` caching: not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Claude-User/1.0; +claude-user@anthropic.com)
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Claude-User/1.0; +claudebot@anthropic.com)
Claude-User
Claude-User (claude-code/2.1.293; +https://support.anthropic.com/)
Claude-User (claude-code/2.1.295; +https://support.anthropic.com/)
Claude-User (claude-code/2.1.296; +https://support.anthropic.com/)
Claude-User (claude-code/2.1.300; +https://support.anthropic.com/)
Claude-User (HAA research client; automated fetch on behalf of a user; honours robots.txt)
```

Anthropic does not publish full user agent strings, only the token.

The string `Claude-User (HAA research client; automated fetch on behalf of a user; honours
robots.txt)` does not follow the format of Anthropic's strings above. It is not Anthropic's
documented user agent. Any client can send the `Claude-User` name.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Claude by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `*/*` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: Claude-User
Disallow: /
```

This token is independent of `ClaudeBot` (training) and `Claude-SearchBot` (search).

## IP ranges and verification

Anthropic publishes one list for all its crawlers: https://claude.com/crawling/bots.json (JSON,
`prefixes` array of `ipv4Prefix` objects, 38 IPv4 prefixes on 2026-10-15). See `claudebot.md`. No
reverse DNS hostnames are published.

The `Claude-User (claude-code/...)` strings come from Claude Code, which runs on the user's own
computer. Anthropic does not document those requests as coming from the published ranges.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Reverse DNS hostnames:

- `*.bc.googleusercontent.com` (forward-confirmed, addresses in the published ranges)

## Hyperwatch

`@hyperwatch/useragent` returns the family `Claude-User` for the `Mozilla/5.0 ... Claude-User/1.0`
strings, for the bare `Claude-User` and for the "HAA research client" string. It returns the
family `claude-code` for the `Claude-User (claude-code/<version>; ...)` strings.

`src/modules/identity.js` sets the identity `Claude` for the family `Claude-User` when the address
is in `src/data/claude-bot-ips.json`, Hyperwatch's copy of Anthropic's list. The family
`claude-code` has no rule and gets no identity.

## Misc

See `claudebot.md` and `claude-searchbot.md` for Anthropic's other robots.

## Sources

- https://support.claude.com/en/articles/8896518-does-anthropic-crawl-the-web (checked 2026-10-15)
- https://claude.com/crawling/bots.json (checked 2026-10-15)
