---
name: Kaspersky CEREBRO
operator: Kaspersky
website: https://www.kaspersky.com
documentation: https://eugene.kaspersky.com/2016/10/04/features-youd-normally-never-hear-about-2017-reboot/
category: other
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: null
  identity: Kaspersky
last_checked: 2026-11-19
---

# Kaspersky CEREBRO

## Description

CEREBRO is a crawler of Kaspersky, the security software company. In a 2016 post on his blog,
Kaspersky's CEO Eugene Kaspersky wrote that "one of our new robots, called CEREBRO, surfs the
Internet all day and night scanning for malicious code"; when it finds some, it "automatically
categorizes it based on its content and sends the info on it to KSN" (Kaspersky Security Network),
"where other robots – also automatically – can apply protection for you". The blog says it reflects
his private position, not the company's official one.

Kaspersky's Web Filter page says its URL classification "is supported by web crawling", alongside
expert systems, content analysts, heuristics, partner intelligence and Kaspersky Security Network
telemetry, without naming the crawler.

## Behavior

The 2016 post says CEREBRO "has already scanned around a hundred million webpages (and doesn't
forget to keep rechecking them, just in case something's changed)".

Paths requested, rate, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Not documented. Kaspersky gives no user agent string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Kaspersky names no `robots.txt` token, does not say whether CEREBRO reads
`robots.txt`, and documents no opt-out.

## IP ranges and verification

None published. Kaspersky documents no IP list, reverse DNS names or ASN for CEREBRO.

Not documented, from a DNS check on 2026-11-19: addresses of AS200107 (Kaspersky Lab Switzerland
GmbH) have reverse DNS names `cerebro-sdc-prod-<N>.kaspersky-labs.com`; of the three found, two
are forward-confirmed and one is not (its name doesn't resolve back to the address). That these
names belong to CEREBRO is inferred from their name only.

## Hyperwatch

No user agent is documented, so no agent family can be given.

In Hyperwatch `main` (after 5.7.0, not released yet), the "hostname only" fallback sets the identity
`Kaspersky` on a forward-confirmed hostname matching `cerebro-*.kaspersky-labs.com`, whatever the
user agent.

## Misc

Nothing else documented.

## Sources

- https://eugene.kaspersky.com/2016/10/04/features-youd-normally-never-hear-about-2017-reboot/ (checked 2026-11-19)
- https://www.kaspersky.com/web-filter (checked 2026-11-19)
- https://rdap.org/ip/77.74.176.0 (RIPE registration of Kaspersky Lab Switzerland GmbH, checked 2026-11-19)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
