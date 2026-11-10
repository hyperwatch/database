---
name: ElevenlabsCrawler
operator: ElevenLabs
website: https://elevenlabs.io
documentation: https://elevenlabs.io/docs/bots
category: ai-training
robots_txt_token: ElevenlabsCrawler
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: ElevenlabsCrawler
  identity: null
last_checked: 2026-11-10
---

# ElevenlabsCrawler

## Description

ElevenlabsCrawler is ElevenLabs' web crawler. It collects public content that may be used to train
ElevenLabs' generative AI models.

## Behavior

ElevenLabs says a `Disallow` for ElevenlabsCrawler means the site's content should not be used for
training, and that `robots.txt` changes are reflected within about 24 hours. Crawl rate,
`Crawl-delay` support and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; ElevenlabsCrawler/1.0; +https://elevenlabs.io/docs/bots)
```

ElevenLabs says the version number may change.

## Observed HTTP headers

Based on dozens of requests seen on 2026-11-10, all pages, from one address on a hosting network.
With no way to verify the crawler, they may not all come from ElevenLabs.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8` (100%) |
| `accept-language` | `en-US,en;q=0.9,*;q=0.8` (100%) |

## Blocking with robots.txt

```
User-agent: ElevenlabsCrawler
Disallow: /
```

The `ElevenlabsCrawler` and `ElevenlabsBot` settings are independent: a site can allow one and
disallow the other.

## IP ranges and verification

None published. No reverse DNS hostnames or ASN are documented, and ElevenLabs gives no way to
verify the crawler.

### Observed

Requests with this user agent seen between 2026-11-07 and 2026-11-10, compared with what the operator publishes. Only differences are listed.

Tens of thousands of requests a day from thousands of addresses, nearly all on hosting and proxy
networks, a few dozen requests per address.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS203020 HostRoyale Technologies Pvt Ltd: `178.251.236.0/24`, `198.13.198.0/24`, `14.102.124.0/24`, `128.121.243.0/24`, `173.254.216.0/24`, `114.69.251.0/24`, `104.223.61.0/24`, `104.204.203.0/24`, and 560 more
- AS207990 HostRoyale Technologies Pvt Ltd: `104.200.71.0/24`, `93.180.239.0/24`, `185.251.250.0/24`, `188.212.143.0/24`, `213.188.92.0/24`, `92.255.87.0/24`, `43.252.31.0/24`, `119.12.180.0/24`, and 426 more
- AS20473 The Constant Company, LLC: `222.167.103.0/24`, `193.37.202.0/24`, `152.39.163.0/24`, `185.217.25.0/24`, `222.167.119.0/24`, `136.242.118.0/24`, `203.168.147.0/24`, `207.45.28.0/24`, and 292 more
- AS30058 FDCservers.net: `72.63.215.0/24`, `72.63.247.0/24`, `72.63.18.0/24`, `72.63.214.0/24`, `205.188.101.0/24`, `72.63.39.0/24`, `72.63.246.0/24`, `72.63.22.0/24`, and 1 more
- AS46635 AviationAI: `9.249.182.0/24`, `9.249.177.0/24`, `69.30.87.0/24`, `9.151.206.0/24`, `9.249.190.0/24`, `9.249.176.0/24`, `9.249.180.0/24`, `9.249.181.0/24`, and 3 more
- AS396356 Latitude.sh: `151.241.118.0/24`, `151.244.13.0/24`, `151.241.124.0/24`, `151.244.53.0/24`, `151.240.225.0/24`, `68.167.150.0/24`, `151.244.104.0/24`, `151.244.35.0/24`, and 46 more
- AS9009 M247 Europe SRL: `5.183.240.0/24`, `83.150.220.0/24`, `83.150.223.0/24`, `92.119.26.0/24`, `104.164.124.0/24`, `45.81.118.0/24`, `92.119.25.0/24`, `154.13.217.0/24`, and 6 more
- AS46261 QuickPacket, LLC: `216.158.200.0/24`, `154.37.102.0/24`, `45.33.155.0/24`, `107.161.113.0/24`, `216.158.197.0/24`, `154.17.132.0/24`, `154.37.96.0/24`, `154.37.111.0/24`, and 34 more
- AS11798 Ace Data Centers, Inc.: `23.26.15.0/24`, `201.14.250.0/24`, `2.26.155.0/24`
- AS10557 Connect Northwest Internet Services, LLC: `94.156.145.0/24`, `94.156.62.0/24`, `203.78.161.0/24`
- AS64249 Charles River Operation: `198.145.143.0/24`, `79.98.182.0/24`
- AS62874 Web2Objects LLC: `72.63.75.0/24`, `72.63.117.0/24`
- AS204287 HostRoyale Technologies Pvt Ltd: `104.194.202.0/24`, `104.143.86.0/24`, `45.41.184.0/24`, `104.143.87.0/24`, `45.41.191.0/24`, `167.160.36.0/24`, `45.41.190.0/24`, `167.160.37.0/24`, and 8 more
- AS201207 Getechbrothers, MB: `66.95.202.0/24`
- AS201341 trafficforce, UAB: `212.52.15.0/24`
- AS18779 EGIHosting: `192.177.101.0/24`
- AS11426 Charter Communications Inc (not a hosting network: prefixes not listed)
- AS396982 Google LLC: `34.33.5.0/24`
- AS263735 SOCIEDAD BUENA HOSTING, S.A.: `181.177.123.0/24`
- AS10753 Level 3 Parent, LLC (not a hosting network: prefixes not listed)

## Hyperwatch

`@hyperwatch/useragent` returns the family `ElevenlabsCrawler`. `src/modules/identity.js` has no
rule for it, so Hyperwatch sets no identity, and with no published list or hostname it cannot.

## Misc

ElevenLabs' second robot is [ElevenlabsBot](elevenlabsbot.md), which fetches pages for its
customers' agents.

## Sources

- https://elevenlabs.io/docs/bots (checked 2026-11-10)
