---
name: bnf.fr_bot
operator: Bibliothèque nationale de France (BnF)
website: https://www.bnf.fr
documentation: https://www.bnf.fr/fr/capture-de-votre-site-web-par-le-robot-de-la-bnf
category: archive
robots_txt_token: bnf.fr_bot
respects_robots_txt: no
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: bnf.fr bot
  identity: BnF.fr
last_checked: 2026-11-10
---

# bnf.fr_bot

## Description

bnf.fr_bot is the crawler of the Bibliothèque nationale de France. It collects websites for the
legal deposit of the internet, set by the French Code du patrimoine since the DADVSI law of
1 August 2006.

## Behavior

The BnF uses the Heritrix crawler. It leaves long delays between two requests so as not to burden
servers. Heritrix does not fully interpret JavaScript and can generate false URLs from it; the BnF
says it filters these as much as it can. Exact crawl rate and `Crawl-delay` support are not
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; bnf.fr_bot; +http://www.bnf.fr/fr/outils/a.dl_web_capture_robot.html) Firefox/57
```

The BnF page gives only the beginning, `Mozilla/5.0 (compatible; bnf.fr_bot; …)`. The full string
comes from Known Agents.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-11-10, all paths (`robots.txt` and pages), verified as BnF.fr by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/xml, application/xml, application/xhtml+xml, text/html; q=0.9, text/plain; q=0.8, image/png, */*; q=0.5` (100%) |
| `accept-language` | `fr, en; q=0.3` (100%) |
| `from` | `robot@bnf.fr` (100%) |

## Blocking with robots.txt

```
User-agent: bnf.fr_bot
Disallow: /
```

The BnF says the Code du patrimoine (art. L132-2-1) allows it not to follow `robots.txt`, and that
it may capture files excluded by `robots.txt` (images, style sheets) when they are needed to
rebuild a site. It does not say that it obeys `robots.txt` otherwise. Site owners whose
performance suffers can write to robot@bnf.fr.

## IP ranges and verification

None published. No hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `bnf.fr bot`. In Hyperwatch `main`
(after 5.4.0), `src/modules/identity.js` sets the identity `BnF.fr` on the forward-confirmed
hostname `robot*-depot-legal-web.bnf.fr`. The BnF documents no hostname: the pattern is
Hyperwatch's own.

## Misc

Nothing else documented.

## Sources

- https://www.bnf.fr/fr/capture-de-votre-site-web-par-le-robot-de-la-bnf (checked 2026-10-15)
- https://knownagents.com/agents/bnf-fr-bot (checked 2026-10-15)
