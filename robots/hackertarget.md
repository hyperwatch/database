---
name: HackerTarget
operator: Hacker Target Pty Ltd
website: https://hackertarget.com
documentation: http://survey07.hackertarget.io/
category: research
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: reverse-dns
  ip_list: null
  hostnames: ["survey*.hackertarget.io"]
hyperwatch:
  family: null
  identity: HackerTarget
last_checked: 2026-11-19
---

# HackerTarget

## Description

HackerTarget's internet survey is "a computer security research project conducted by Hacker Target
Pty Ltd", the company behind the `hackertarget.com` security tools. The survey makes "a number of
harmless attempts to connect to every live IPv4 address", periodically, and the data is made
available to security researchers and used by organisations to understand the security of their own
public-facing networks.

## Behavior

The survey page says no attempt is ever made to exploit security issues, guess passwords or change
configurations, and only publicly available information is surveyed, "typically" the service banner
of common TCP ports (such as identifying a web server technology).

Paths requested, rate, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Not documented. The survey page gives no user agent string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: HackerTarget names no `robots.txt` token and does not say whether the survey reads
`robots.txt`.

To opt out of future surveys, email `survey-admin` at `hackertarget.com` with the IP address or CIDR
netblock.

## IP ranges and verification

No IP list is published. The survey page says "all survey machines have a reverse DNS entry that
resolves to survey##.hackertarget.io". It does not say to confirm the name with a forward lookup. No
ASN is documented.

Not documented, from a DNS check on 2026-11-19: `survey05`, `survey06` and `survey07.hackertarget.io`
resolve to addresses whose reverse DNS is the same name (forward-confirmed), in AS14061
(DigitalOcean). `survey11`, `survey12` and `survey13.hackertarget.io` resolve, but their addresses
had no reverse DNS name. `hackertarget.io` redirects to `survey05.hackertarget.io`, and each survey
host serves the survey page.

## Hyperwatch

No user agent is documented, so no agent family can be given.

In Hyperwatch `main` (after 5.7.0, not released yet), the "hostname only" fallback sets the identity
`HackerTarget` on a forward-confirmed hostname matching `survey*.hackertarget.io`, whatever the user
agent.

## Misc

The same page is served by each survey host; on 2026-11-19 the copy on `survey07` still named
`survey05.hackertarget.io` in its heading.

## Sources

- http://survey07.hackertarget.io/ (checked 2026-11-19)
- http://survey05.hackertarget.io/ (redirect from http://hackertarget.io/, checked 2026-11-19)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
