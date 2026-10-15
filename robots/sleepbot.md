---
name: SleepBot
operator: Unknown
website: http://sleepbot.com
documentation: null
category: unknown
robots_txt_token: SleepBot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: SleepBot
  identity: SleepBot
last_checked: 2026-10-15
---

# SleepBot

## Description

SleepBot points to `http://sleepbot.com/` in its user agent. That site is "Sleepbot Constructs", a
personal site launched in 1995 (ambient music archive, streaming station, old projects). Its home
page does not mention a crawler. No other source from an operator was found, so the operator and
purpose are not confirmed.

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; SleepBot/1.0; +http://sleepbot.com/) Chrome/131.0.0.0 Safari/537.36
```

This string comes from Known Agents.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SleepBot
Disallow: /
```

The token is taken from the user agent. Whether the robot obeys `robots.txt` is not documented.

## IP ranges and verification

None published.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `SleepBot`. Hyperwatch sets the identity
`SleepBot` when the reverse DNS name ends with `.googleusercontent.com`. This is a cloud hostname:
any Google Cloud customer passes it. The hostname is also not confirmed by a forward lookup.
Nothing from an operator supports the check.

## Misc

The sleepbot.com home page links a sleep-tracking app, SleepBot, at mySleepBot.com. Nothing links
that app to this robot.

## Sources

- http://sleepbot.com/ (checked 2026-10-15)
- https://knownagents.com/agents/sleepbot (checked 2026-10-15)
