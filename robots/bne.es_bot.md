---
name: bne.es_bot
operator: Biblioteca Nacional de España (BNE), Archivo de la Web Española
website: https://www.bne.es
documentation: https://www.bne.es/es/colecciones/archivo-web-espanola/aviso-webmasters
category: archive
robots_txt_token: bne.es_bot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: bne.es bot
  identity: null
last_checked: 2026-11-10
---

# bne.es_bot

## Description

bne.es_bot is the crawler of the Archivo de la Web Española (Spanish Web Archive), run by the
Biblioteca Nacional de España (BNE), Spain's national library, to preserve Spanish websites.

The BNE's notice to webmasters (linked from the user agent) answered `403` to automated fetches on
2026-11-10, so nothing here comes from it. The description is from the user agent and the
third-party directories below.

## Behavior

Not documented in a source that could be read. Crawl rate, `Crawl-delay` support and JavaScript
rendering are unknown.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; bne.es_bot; https://www.bne.es/es/colecciones/archivo-web-espanola/aviso-webmasters) Firefox/129.0.1
```

Third-party directories also list `Mozilla/5.0 (compatible; bne.es_bot; +https://www.bne.es/es/colecciones/archivo-web-espanola/aviso-webmasters)`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: bne.es_bot
Disallow: /
```

The token is taken from the user agent; the BNE's own rules could not be read. Third-party
directories disagree: one says the crawler follows `robots.txt`, another that collection under
legal deposit may not. The BNE does not confirm either in a source that could be read.

## IP ranges and verification

None found. No IP list, reverse DNS hostnames or ASN could be read from the BNE.

### Observed

Requests with this user agent seen between 2026-11-07 and 2026-11-10, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS200521 Ministerio de Transformacion Digital y de la Funcion Publica: `212.128.118.0/24`

## Hyperwatch

`@hyperwatch/useragent` returns the family `bne.es bot`. `src/modules/identity.js` has no rule for
it, so Hyperwatch sets no identity.

## Misc

The BnF's [bnf.fr_bot](bnf.fr_bot.md) and the British Library's
[bl.uk_lddc_bot](bl.uk_lddc_bot.md) are the French and British counterparts.

## Sources

- https://www.bne.es/es/colecciones/archivo-web-espanola/aviso-webmasters (checked 2026-11-10: `403` to automated fetches)
- https://knownagents.com/agents/bne-es-bot (according to search results, 2026-11-10)
- https://botcrawl.com/bots/biblioteca-nacional-de-espana-web-archive-crawler/ (according to search results, 2026-11-10)
