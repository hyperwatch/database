---
name: Mail.RU_Bot
operator: Mail.ru (by the link in its user agent; documentation not available)
website: https://mail.ru
documentation: null
category: unknown
robots_txt_token: Mail.RU_Bot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Mail.RU Bot
  identity: Mail.RU
last_checked: 2026-10-15
---

# Mail.RU_Bot

## Description

Mail.RU_Bot is a robot whose user agent links to Mail.ru's search help. Its documentation pages,
https://help.mail.ru/webmaster/indexing/robots and http://go.mail.ru/help/robots, both redirect to
the home page of Mail.ru's help center on 2026-10-15, and no page about the robot was found there.
Its purpose is not documented. This file also covers the `Img` and `Fast` variants that Hyperwatch
groups with it.

## Behavior

Not documented. Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` handling
are unknown.

## User agents

No string from Mail.ru could be fetched. Third-party sources give two:

```
Mozilla/5.0 (compatible; Mail.RU_Bot/2.0; +http://go.mail.ru/bot)
Mozilla/5.0 (compatible; Linux x86_64; Mail.RU_Bot/Robots/2.0; +http://go.mail.ru/help/robots)
```

The first is from CL SEO, the second from Known Agents. No source with a full `Img` or `Fast`
string was found.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented by Mail.ru. According to Known Agents, which says the robot is not expected to follow
`robots.txt`:

```
User-agent: Mail.RU_Bot
Disallow: /
```

## IP ranges and verification

None found. No Mail.ru page with an IP list, reverse DNS hostnames or ASN could be fetched.

## Hyperwatch

`@hyperwatch/useragent` parses the CL SEO string as family `Mail.RU Bot` and the Known Agents
string as `Mail.RU Bot Robots`. In Hyperwatch `main` (after 5.3.3), `src/modules/identity.js` sets
the identity `Mail.RU` for the families `Mail.RU Bot`, `Mail.RU Bot Img`, `Mail.RU Bot Fast` and
`Mail.RU Bot Robots` when the unconfirmed hostname ends with `.go.mail.ru`. Mail.ru's suffix could
not be checked against its documentation, and the check is not forward-confirmed.

## Misc

Nothing else documented.

## Sources

- https://help.mail.ru/webmaster/indexing/robots (checked 2026-10-15, redirects to https://help.mail.ru/)
- http://go.mail.ru/help/robots (checked 2026-10-15, redirects to https://help.mail.ru/)
- https://knownagents.com/agents/mail-ru-bot (checked 2026-10-15)
- https://chrisleverseo.com/user-agents/mail-ru-bot/ (checked 2026-10-15)
