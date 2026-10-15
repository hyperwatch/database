---
name: OAI-SearchBot
operator: OpenAI
website: https://openai.com
documentation: https://developers.openai.com/api/docs/bots
category: ai-search
robots_txt_token: OAI-SearchBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://openai.com/searchbot.json
  hostnames: []
hyperwatch:
  family: OAI-SearchBot
  identity: OpenAI SearchBot
last_checked: 2026-10-15
---

# OAI-SearchBot

## Description

OAI-SearchBot is run by OpenAI. It finds and fetches pages so they can be shown in the search
features of ChatGPT. It is separate from GPTBot, which collects training data, and from
ChatGPT-User, which fetches pages on a user's request.

## Behavior

OpenAI says that sites opted out of OAI-SearchBot are not shown in ChatGPT search answers. They
can still appear as plain navigational links. OpenAI says it can take about 24 hours after a
`robots.txt` change for its systems to adjust. If a site allows both OAI-SearchBot and GPTBot,
OpenAI may use the results of one crawl for both purposes.

When it fetches `robots.txt`, the robot may add a `robots.txt;` marker to its user agent, so these
requests can be told apart from page fetches.

Crawl rate, `Crawl-delay` support and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36; compatible; OAI-SearchBot/1.0; +https://openai.com/searchbot
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36; compatible; OAI-SearchBot/1.4; +https://openai.com/searchbot
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36; compatible; OAI-SearchBot/1.4; robots.txt; +https://openai.com/searchbot
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; OAI-SearchBot/1.0; +https://openai.com/searchbot
```

OpenAI documents the suffix `compatible; OAI-SearchBot/1.4; +https://openai.com/searchbot` after
a browser-style prefix, and says the version number may change.

## Observed HTTP headers

Based on dozens of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as OpenAI SearchBot by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `*/*` (100%) |
| `from` | `oai-searchbot(at)openai.com` (100%) |
| `referer` | `(present)` (53%) |
| `x-openai-host-hash` | `(present)` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: OAI-SearchBot
Disallow: /
```

Each OpenAI token is set independently. Blocking OAI-SearchBot does not block GPTBot (training)
and the reverse. OpenAI recommends using OAI-SearchBot, not ChatGPT-User, to manage search
opt-outs.

## IP ranges and verification

OpenAI publishes the source ranges at https://openai.com/searchbot.json. The file is JSON with a
`creationTime` field and a `prefixes` array of objects with an `ipv4Prefix` key. On 2026-10-15 it
held 39 IPv4 prefixes and was dated 2026-01-02. No reverse DNS hostnames or ASN are documented.


## Hyperwatch

`@hyperwatch/useragent` parses all the strings above as family `OAI-SearchBot`. Hyperwatch sets the
identity `OpenAI SearchBot` when the client address is inside the ranges of
`src/data/openai-searchbot-ips.json`, a copy of OpenAI's list refreshed by
`node scripts/fetch-ips.js` (in Hyperwatch `main` (after 5.3.3), 39 ranges, the same as the
published list on 2026-10-15).

## Misc

OpenAI runs three robots with separate tokens: GPTBot (training), OAI-SearchBot (search) and
ChatGPT-User (user-initiated fetches). Each has its own IP list.

## Sources

- https://developers.openai.com/api/docs/bots (checked 2026-10-15)
- https://openai.com/searchbot.json (checked 2026-10-15)
