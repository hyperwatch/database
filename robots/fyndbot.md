---
name: fyndbot
operator: Fynd
website: https://fynd.bot
documentation: null
category: search-engine
robots_txt_token: fyndbot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: fyndbot
  identity: null
last_checked: 2026-10-15
---

# fyndbot

## Description

fyndbot is the crawler of Fynd, a web and image search engine at https://fynd.bot. The operator
publishes no page about the robot. Third-party bot directories describe it as the crawler that
discovers and refreshes pages for the Fynd index.

## Behavior

Not documented by the operator. The user agents seen carry a purpose in parentheses: `robots` when
fetching `robots.txt` and `page-validation` when checking pages.

## User agents

```
fyndbot (page-validation; https://fynd.bot)
fyndbot (robots; https://fynd.bot)
```

Known Agents also lists `fyndbot (crawler; https://fynd.bot)`, and a `recrawler` variant.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: fyndbot
Disallow: /
```

The operator does not document a token. `fyndbot` is the product name in its user agent and the
token used by third-party directories.

## IP ranges and verification

None published. No reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `fyndbot`. `src/modules/identity.js` has no
rule for it, so it gets no identity.

## Misc

Known Agents also lists FyndSearchEngine-Crawler and FyndSearchEngine-ReCrawler under the same
operator. `https://fynd.bot/robots.txt` returned 404 when checked.

## Sources

- https://fynd.bot (checked 2026-10-15)
- https://knownagents.com/agents/fyndbot (checked 2026-10-15)
