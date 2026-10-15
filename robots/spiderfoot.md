---
name: SpiderFoot
operator: Intel 471 (SpiderFoot HX); the open-source version is run by its users
website: https://www.spiderfoot.net
documentation: https://github.com/smicallef/spiderfoot
category: other
robots_txt_token: null
respects_robots_txt: no
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Firefox
  identity: SpiderFoot
last_checked: 2026-10-15
---

# SpiderFoot

## Description

SpiderFoot is an open-source intelligence (OSINT) automation tool, used for threat intelligence,
attack surface mapping and investigations. It exists as open-source software on GitHub, which
anyone can run, and as a commercial cloud service, SpiderFoot HX. Intel 471 announced on
2022-11-02 that it had acquired SpiderFoot. On 2026-10-15, `https://www.spiderfoot.net/`
redirected to `https://www.intel471.com/`.

## Behavior

A SpiderFoot scan queries many sources about a target and, through its spider module, fetches the
target's web pages and follows links. In the open-source code (`modules/sfp_spider.py`), the
option "Only follow links specified by robots.txt?" (`robotsonly`) is off by default. When it is
on, SpiderFoot reads `/robots.txt` and skips every link matching any `Disallow` line, without
looking at `User-agent` lines (the parser's comment lists "Check and parse User-Agent" as a to-do).

The number of pages and link depth are scan options. Crawl rate and `Crawl-delay` are not
documented. The behavior of SpiderFoot HX is not documented publicly.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:62.0) Gecko/20100101 Firefox/62.0
```

This is the default `_useragent` of the open-source version (`sf.py`). It is an ordinary Firefox
62 string with no mention of SpiderFoot. Users can change it, or load a list of user agents to
pick from at random for each request. The user agent of SpiderFoot HX is not documented.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

There is no token. `robots.txt` is ignored unless the user turns on `robotsonly`, and then every
`Disallow` line applies, whatever its `User-agent`:

```
User-agent: *
Disallow: /
```

## IP ranges and verification

None published. The open-source version runs from its users' own machines. No IP list or reverse
DNS names are documented for SpiderFoot HX.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Firefox` for the default string, so no rule by family
applies. Hyperwatch sets the identity `SpiderFoot` in two fallbacks of `src/modules/identity.js`,
for requests of any family that have no identity yet:

- unconfirmed hostname ending with `.hx.spiderfoot.net`: whoever controls the address's reverse
  DNS can set it. This suffix is not documented by SpiderFoot or Intel 471.
- signature `6877bffcee5eb4b80f4f974d7697e809`: an MD5 fingerprint of the `accept`, `accept-charset`,
  `accept-language`, `dnt`, `from` and `user-agent` headers (`src/modules/signature.js`). Any client sending the same headers matches it.

Neither check verifies the source. The open-source version cannot be verified at all, as it runs
anywhere.

## Misc

The source code is at https://github.com/smicallef/spiderfoot (version 4.0 on 2026-10-15). Intel
471 said it would integrate SpiderFoot's capabilities into its TITAN platform.

## Sources

- https://github.com/smicallef/spiderfoot (README, `sf.py`, `modules/sfp_spider.py`, `spiderfoot/helpers.py`, checked 2026-10-15)
- https://www.spiderfoot.net/ (redirects to https://www.intel471.com/, checked 2026-10-15)
- https://intel471.com/company/press-releases/intel-471-acquires-spiderfoot (checked 2026-10-15)
