---
name: AzureAI-SearchBot
operator: Microsoft (by its name; not confirmed by Microsoft documentation)
website: https://azure.microsoft.com
documentation: null
category: unknown
robots_txt_token: AzureAI-SearchBot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: AzureAI-SearchBot
  identity: null
last_checked: 2026-10-15
---

# AzureAI-SearchBot

## Description

AzureAI-SearchBot is a user agent whose name points to Microsoft Azure AI (Azure AI Search is
Microsoft's managed search and retrieval service). No Microsoft page describing this user agent was
found: its operator, purpose and the product it serves are not documented. Third-party bot
directories list it as a Microsoft crawler for AI search, without citing a Microsoft source.

## Behavior

Not documented. Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` handling
are unknown.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; AzureAI-SearchBot/1.0;
```

The string has no URL or contact address.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: AzureAI-SearchBot
Disallow: /
```

This uses the name in the user agent. Whether the robot reads `robots.txt`, and which tokens it
obeys, is not documented.

## IP ranges and verification

None published. No IP list, reverse DNS names or ASN are documented for this user agent. Bing's
`bingbot.json` list covers bingbot only.

## Hyperwatch

`@hyperwatch/useragent` returns the family `AzureAI-SearchBot`. `src/modules/identity.js` has no
rule for it, so Hyperwatch sets no identity.

## Misc

Nothing documented. Microsoft's Bing crawlers (bingbot, adidxbot, MicrosoftPreview) are separate.

## Sources

- https://learn.microsoft.com/en-us/azure/search/search-what-is-azure-search (checked 2026-10-15, does not mention the user agent)
- https://botcrawl.com/bots/azureai-searchbot/ (checked 2026-10-15, third-party)
