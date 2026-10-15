---
name: ChatGPT-User
operator: OpenAI
website: https://openai.com
documentation: https://developers.openai.com/api/docs/bots
category: ai-assistant
robots_txt_token: ChatGPT-User
respects_robots_txt: partial
verification:
  method: ip-list
  ip_list: https://openai.com/chatgpt-user.json
  hostnames: []
hyperwatch:
  family: ChatGPT-User
  identity: ChatGPT
last_checked: 2026-10-15
---

# ChatGPT-User

## Description

ChatGPT-User is run by OpenAI. It fetches web pages for actions started by a user in ChatGPT and
in Custom GPTs, for example when a user asks a question and ChatGPT visits a page to answer it.
It is also used by GPT Actions to reach external applications.

## Behavior

OpenAI says ChatGPT-User is not used for automatic crawling. It is not used to decide whether
content may appear in ChatGPT search. Because the requests are started by a user, OpenAI says
`robots.txt` rules may not apply.

Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` caching are not
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; ChatGPT-User/1.0; +https://openai.com/bot
```

OpenAI documents a string ending in `compatible; ChatGPT-User/1.0; +https://openai.com/bot`.

## Observed HTTP headers

Only header signatures are available (they keep `accept`, `accept-language` and `dnt`), from fewer than 10 distinct signatures seen on 2026-10-15:

- `accept`: `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9`
- `accept-language`: `en-US,en;q=0.9`
- `dnt`: never sent

## Blocking with robots.txt

```
User-agent: ChatGPT-User
Disallow: /
```

OpenAI says `robots.txt` rules may not apply to these user-initiated requests. For search
opt-outs and automatic crawling, OpenAI points to the OAI-SearchBot token.

## IP ranges and verification

OpenAI publishes the source ranges at https://openai.com/chatgpt-user.json. The file is JSON with
a `creationTime` field and a `prefixes` array of objects with an `ipv4Prefix` key. On 2026-10-15
it held 234 IPv4 prefixes and was dated 2026-10-07. No reverse DNS hostnames or ASN are
documented.


## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `ChatGPT-User`. Hyperwatch sets the
identity `ChatGPT` when the client address is inside the ranges of
`src/data/chatgpt-user-ips.json`, a copy of OpenAI's list refreshed by
`scripts/fetch-openai-ips.js`.

## Misc

Related robots from OpenAI: GPTBot (training) and OAI-SearchBot (search), each with its own token
and IP list.

## Sources

- https://developers.openai.com/api/docs/bots (checked 2026-10-15)
- https://openai.com/chatgpt-user.json (checked 2026-10-15)
