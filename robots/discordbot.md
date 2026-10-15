---
name: Discordbot
operator: Discord
website: https://discord.com
documentation: https://support.discord.com/hc/en-us/articles/42500550752919-About-Discord-Link-Previews-and-the-Discordbot
category: social-preview
robots_txt_token: Discordbot
respects_robots_txt: unknown
verification:
  method: ip-list
  ip_list: https://cdn.discordapp.com/ipranges/discord.json
  hostnames: []
hyperwatch:
  family: Discordbot
  identity: Discord
last_checked: 2026-10-15
---

# Discordbot

## Description

Discordbot is Discord's link preview fetcher. When a link is shared in a Discord message, it visits
the page to read its title, description and image and build the preview card.

## Behavior

Discord says the robot only visits a link when it is shared in a message: it does not crawl sites
on its own. When a link points to an image or video, Discord may keep a copy for a while and serve
it from its own servers, so the site does not see the viewer's address.

Crawl rate, JavaScript rendering, `Crawl-delay` and `robots.txt` are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; Discordbot/2.0; +https://discordapp.com)
```

Discord says parts of the string other than `Discordbot` may change, and recommends matching the
word `Discordbot` only.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Discordbot
Disallow: /
```

Discord does not say whether Discordbot reads `robots.txt`. The token above is the name in its user
agent.

## IP ranges and verification

Discord says the user agent alone is not enough, and that the address must be in its published
list, which can change. The list is at https://cdn.discordapp.com/ipranges/discord.json (JSON with
`creationTime`, `syncToken`, `notes` and a `prefixes` array of objects with `ipv4Prefix` and
`services`) and at https://cdn.discordapp.com/ipranges/discord.txt (one prefix per line). On
2026-10-15 it held 20 IPv4 prefixes, all `/32`, 12 tagged `media` and 8 tagged `api`, with the note
"discord egress", and was dated 2026-08-04. The list does not say which service fetches link
previews. No reverse DNS hostname or ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Discordbot`. In Hyperwatch `main` (after 5.3.3),
`src/modules/identity.js` sets the identity `Discord` on a cloud hostname ending with
`.googleusercontent.com` or the published list (`discord-ips.json`). The cloud hostname is not
documented by Discord, and any Google Cloud customer passes it.

## Misc

Nothing else documented.

## Sources

- https://support.discord.com/hc/en-us/articles/42500550752919-About-Discord-Link-Previews-and-the-Discordbot
  (the page returned 403; read through the help center API,
  https://support.discord.com/api/v2/help_center/en-us/articles/42500550752919.json, article
  updated 2026-10-14; checked 2026-10-15)
- https://cdn.discordapp.com/ipranges/discord.json (checked 2026-10-15)
- https://cdn.discordapp.com/ipranges/discord.txt (checked 2026-10-15)
