---
name: Riddler
operator: F-Secure (riddler.io is registered to WithSecure Corporation)
website: https://riddler.io
documentation: https://riddler.io/about
category: research
robots_txt_token: Riddler
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Riddler
  identity: Riddler
last_checked: 2026-10-15
---

# Riddler

## Description

Riddler (also called Riddlerbot) is the crawler of riddler.io, which its about page described as
"an online research project which investigates algorithms for mapping the topology of the
Internet". It collected data about public systems by crawling and by mapping common ports. The
page carried "© 2016 F-Secure". On 2026-10-15, the whois record of `riddler.io` named WithSecure
Corporation as registrant.

On 2026-10-15, `riddler.io` did not resolve in DNS, so the about page could not be fetched. What
follows comes from an archived copy dated 2020-03-18. The latest archived copy, from 2024-06-13,
is a CloudFront "403 ERROR" page. Whether the crawler still runs is not documented.

## Behavior

The archived page said:

- "For most sites, Riddlerbot shouldn't access your site more than once every few seconds on
  average", with short bursts possible because of network delays.
- It should download only one copy of each page at a time.
- It runs on several machines, placed near the sites they crawl, so visits can come from several
  machines, all with the user agent `Riddler`.

`Crawl-delay` support, JavaScript rendering and `robots.txt` caching were not documented.

## User agents

Exact strings, one per line:

```
Riddler (http://riddler.io/about)
```

The operator page names the user agent `Riddler` but does not give a full string. This string
comes from the crawler-user-agents list.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Riddler
Disallow: /
```

The archived page said the crawler "is compliant with the robots.txt standard". To exclude a
network from port mapping, it asked owners to write to riddlerio@f-secure.com with the netblock,
whose whois record had to include a valid email address.

## IP ranges and verification

None published. No IP list, reverse DNS names or ASN were documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Riddler`. `src/modules/identity.js` sets the identity
`Riddler` when the unconfirmed hostname ends with `.eu-west-1.compute.amazonaws.com`. This is a
cloud hostname: any customer of Amazon EC2 in eu-west-1 (Ireland) passes. Riddler never
documented running on AWS.

## Misc

Matomo's device-detector lists Riddler as a "Security search bot" produced by F-Secure. According
to a Fedora infrastructure mailing-list thread from 2015, the crawler did not obey `robots.txt` at
the time, despite the statement on its page.

## Sources

- https://riddler.io/about (did not resolve, 2026-10-15)
- https://web.archive.org/web/20200318232653/https://riddler.io/about (checked 2026-10-15)
- https://web.archive.org/web/20240613070149/https://riddler.io/about (checked 2026-10-15)
- `whois riddler.io` (checked 2026-10-15)
- https://raw.githubusercontent.com/monperrus/crawler-user-agents/master/crawler-user-agents.json (checked 2026-10-15)
- https://raw.githubusercontent.com/matomo-org/device-detector/master/regexes/bots.yml (checked 2026-10-15)
- https://lists.stg.fedoraproject.org/archives/list/infrastructure@lists.fedoraproject.org/thread/LER6UPTRLYLZN55HH2SGIE2RWXGX5FA7/ (search result summary, 2026-10-15)
