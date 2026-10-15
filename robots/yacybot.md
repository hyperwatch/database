---
name: yacybot
operator: YaCy users (open-source peer-to-peer search engine project)
website: https://yacy.net
documentation: https://yacy.net/bot.html
category: search-engine
robots_txt_token: yacybot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: yacybot
  identity: null
last_checked: 2026-10-15
---

# yacybot

## Description

yacybot is the crawler of YaCy, a free, open-source, peer-to-peer search engine. There is no
central operator. Anyone can install YaCy and run a peer, and each peer crawls the web on behalf
of the person who runs it. The bot page says the crawlers are "maintained by the YaCy users".
Requests with this user agent therefore come from many unrelated people, on home connections,
servers and cloud machines.

## Behavior

The bot page says yacybot follows `robots.txt` and that "after some hours all yacybots will obey
your instructions". It does not document crawl rate, JavaScript rendering or `robots.txt` caching.

In the YaCy source code, the robots.txt parser reads `Crawl-delay`. The default minimum delay
between two requests to the same host is 250 ms for the internet crawler profile ("YaCy Internet
(cautious)"). Each peer's owner can change crawl settings.

The user agent carries details of the peer: the network name (for example `freeworld`, the public
network, and `global` or `local`), CPU architecture, operating system and kernel version, Java
version, and time zone and language.

## User agents

Exact strings, one per line:

```
yacybot (/global; amd64 Linux 6.18.33.2-microsoft-standard-WSL2; java 24.0.2; Etc/en) https://yacy.net/bot.html
yacybot (/global; amd64 Linux 7.2.9-1-cachyos; java 21.0.12.1; Europe/de) http://yacy.net/bot.html
yacybot (/global; amd64 Windows 11 10.0; java 11.0.21; Asia/en) http://yacy.net/bot.html
yacybot (freeworld-global; amd64 Linux 7.0.0-31-generic; java 24.0.2; Europe/en) https://yacy.net/bot.html
yacybot (freeworld/global; aarch64 Linux 6.18.34+rpt-rpi-2712; java 24.0.2; Etc/en) https://yacy.net/bot.html
yacybot (freeworld/global; amd64 Linux 5.10.0-46-amd64; java 17.0.20.1; Europe/en) https://yacy.net/bot.html
yacybot (freeworld/global; amd64 Linux 6.12.107+deb13-amd64; java 21.0.12.1; Etc/en) https://yacy.net/bot.html
yacybot (freeworld/global; amd64 Linux 6.18.33.2-microsoft-standard-WSL2; java 24.0.2; Etc/en) https://yacy.net/bot.html
yacybot (freeworld/global; amd64 Linux 6.18.54.1-microsoft-standard-WSL2; java 24.0.2; Etc/en) https://yacy.net/bot.html
yacybot (freeworld/global; amd64 Linux 7.2.9-gentoo; java 27; Atlantic/de) https://yacy.net/bot.html
yacybot (freeworld/global; amd64 Linux 7.2.9-gentoo; java 27; Europe/de) https://yacy.net/bot.html
```

The template in the YaCy source is `yacybot ($$SYSTEM$$) https://yacy.net/bot.html`.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: yacybot
Disallow: /
```

The bot page does not name a token. In the source code, the internet and intranet crawler
profiles match the `yacybot` token (case-insensitive exact match on the `User-agent:` value) and
`*`. `Crawl-delay` is parsed.

YaCy also lets a peer owner pick other crawler profiles: a "Googlebot" profile that sends a
Googlebot user agent, a "Random Browser" profile that sends browser user agents, and a custom
agent (which may not contain "yacy"). Requests made with those profiles do not say yacybot and
do not match the `yacybot` token.

## IP ranges and verification

None published. Peers run on any network, so there is no IP list, reverse DNS name or ASN that
identifies yacybot.

## Hyperwatch

`@hyperwatch/useragent` returns the family `yacybot`. `src/modules/identity.js` has no rule for
it, so Hyperwatch sets no identity. With no possible verification, this is expected.

## Misc

- YaCy peers exchange index data with each other (peer-to-peer). Some peers run in the public
  `freeworld` network; others run private networks or intranet search.
- The YaCy forum (forum.yacy.de) is the contact point given on the bot page.

## Sources

- https://yacy.net/bot.html (checked 2026-10-15)
- https://github.com/yacy/yacy_search_server/blob/master/source/net/yacy/cora/protocol/ClientIdentification.java (checked 2026-10-15)
- https://github.com/yacy/yacy_search_server/blob/master/source/net/yacy/crawler/robots/RobotsTxtParser.java (checked 2026-10-15)
- https://github.com/yacy/yacy_search_server/blob/master/defaults/yacy.init (checked 2026-10-15)
