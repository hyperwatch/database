---
name: bl.uk_lddc_bot
operator: British Library (UK legal deposit libraries)
website: https://www.bl.uk
documentation: https://www.bl.uk/services/legal-deposit/web-archiving
category: archive
robots_txt_token: bl.uk_lddc_bot
respects_robots_txt: partial
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: bl.uk lddc bot
  identity: null
last_checked: 2026-10-15
---

# bl.uk_lddc_bot

## Description

bl.uk_lddc_bot is the crawler of the UK Web Archive, run by the British Library with the other UK
legal deposit libraries. Under legal deposit law it collects a yearly snapshot of all the UK
websites it can identify (at least four million sites), plus selective crawls during the year.

## Behavior

The British Library says the crawler starts from a seed list of home pages and follows links down
within the same domain. Politeness rules limit how many levels are crawled and how much is
requested from one site, and leave an interval between requests. It cannot reach content behind a
login. The National Library of Scotland, one of the legal deposit libraries, says the crawler is
Heritrix and cannot interpret `rel=nofollow`. Exact crawl rate, JavaScript rendering and
`Crawl-delay` support are not documented.

## User agents

Exact strings, one per line:

```
bl.uk_lddc_bot/3.4.0-20220727 (+https://www.bl.uk/legal-deposit-web-archiving)
```

The British Library page does not give the user agent. The National Library of Scotland and
Cambridge University Library give the token `bl.uk_lddc_bot`. The full string comes from Known
Agents.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: bl.uk_lddc_bot
Disallow: /
```

The British Library says a site owner "is not required to take any action such as changing the
website's 'robots.txt'". The National Library of Scotland says the crawler "will generally follow"
`robots.txt` but may overrule it, for example to collect JavaScript or CSS, and normally respects
robots meta tags. It warns that blocking the crawler gets in the way of the libraries' legal
obligations.

## IP ranges and verification

None published. No hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `bl.uk lddc bot`. The rule in
`src/modules/identity.js` is for the family `bl.uk ldfc bot` (`ldfc`, not `lddc`), so the
documented crawler never gets the identity `British Library`. No source found documents a
`bl.uk_ldfc_bot` user agent. For a request that did parse as `bl.uk ldfc bot`, the rule checks that
the reverse DNS name ends with `.bl.uk`, without a forward lookup. The British Library does not
document this hostname.

## Misc

The UK Web Archive's public site was inaccessible on 2026-10-15; the British Library says it is
working to restore access and keeps collecting websites in the meantime.

## Sources

- https://www.bl.uk/services/legal-deposit/web-archiving (checked 2026-10-15, reached from https://www.bl.uk/legal-deposit-web-archiving)
- https://www.nls.uk/about-us/who-and-what/legal-deposit/web-harvesting/ (checked 2026-10-15)
- https://www.lib.cam.ac.uk/digitalpreservation/services/web-archiving/creating-preservable-websites (checked 2026-10-15)
- https://www.webarchive.org.uk/ (checked 2026-10-15, FAQ pages redirect to the home page)
- https://knownagents.com/agents/bl-uk-lddc-bot (checked 2026-10-15)
