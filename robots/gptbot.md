---
name: GPTBot
operator: OpenAI
website: https://openai.com
documentation: https://developers.openai.com/api/docs/bots
category: ai-training
robots_txt_token: GPTBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://openai.com/gptbot.json
  hostnames: []
hyperwatch:
  family: GPTBot
  identity: OpenAI GPTBot
last_checked: 2026-10-15
---

# GPTBot

## Description

GPTBot is OpenAI's crawler for model training. OpenAI says it is used to make its generative AI
foundation models more useful and safe. Disallowing it signals that a site's content should not
be used for training.

## Behavior

- `robots.txt`: GPTBot obeys rules for the `GPTBot` token. OpenAI may add a `robots.txt` marker to
  the user agent when it fetches `robots.txt`.
- OpenAI says it can take about 24 hours for its systems to adjust to a `robots.txt` change. This
  is stated in the context of search.
- If both GPTBot and OAI-SearchBot are allowed, OpenAI may use the results of one crawl for both
  purposes.
- Crawl rate, `Crawl-delay` and JavaScript rendering: not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; GPTBot/1.4; +https://openai.com/gptbot
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; GPTBot/1.4; +https://openai.com/gptbot)
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; GPTBot/1.0; +https://openai.com/gptbot)
```

The first string is the one OpenAI documents. OpenAI says the version number may change.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: GPTBot
Disallow: /
```

OpenAI's tokens are independent. Blocking GPTBot does not block `OAI-SearchBot` (search in
ChatGPT), `OAI-AdsBot` (ad landing page checks) or `ChatGPT-User` (user-initiated fetches, for
which OpenAI says `robots.txt` rules may not apply).

## IP ranges and verification

OpenAI publishes GPTBot's addresses at https://openai.com/gptbot.json. It is a JSON object with
`creationTime` and `prefixes`, an array of objects with an `ipv4Prefix` key in CIDR notation. On
2026-10-15 it held 18 IPv4 prefixes (creation time 2026-09-22), no IPv6.

No reverse DNS hostnames are published.

## Hyperwatch

`@hyperwatch/useragent` returns the family `GPTBot` for all three strings.
`src/modules/identity.js` sets the identity `OpenAI GPTBot` when the address is in
`src/data/gptbot-ips.json`, a copy of OpenAI's list refreshed by `scripts/fetch-openai-ips.js`
(18 entries on 2026-10-15).

## Misc

OpenAI publishes separate lists for its other robots: https://openai.com/searchbot.json
(OAI-SearchBot), https://openai.com/chatgpt-user.json (ChatGPT-User) and
https://openai.com/adsbot.json (OAI-AdsBot). `https://openai.com/gptbot`, the URL in the user
agent, returned HTTP 403 to an automated fetch on 2026-10-15.

## Sources

- https://developers.openai.com/api/docs/bots (checked 2026-10-15)
- https://openai.com/gptbot.json (checked 2026-10-15)
- https://openai.com/gptbot (checked 2026-10-15)
