# Hyperwatch identities

Every identity set by Hyperwatch `main` at `bbb603e` (`src/modules/identity.js`, after 5.3.3, not
released yet), checked 2026-10-16: the agent
families leading to it, what is checked, and the robot files it covers. The terms in "Check" are
defined in [`AGENTS.md`](AGENTS.md#hyperwatch-section). "Hostname only" and "signature" are the
fallbacks applied to any user agent when no family rule matched. "Published list" means a list in
`src/data/` refreshed by `node scripts/fetch-ips.js`, unless it says "copied by hand".

| Identity | Agent families | Check | Robot files |
|---|---|---|---|
| 360Spider | `360Spider` | published list (`360spider-ips.json`, copied by hand) | [360Spider](robots/360spider.md) |
| Ahrefs | `AhrefsBot`, `AhrefsSiteAudit` | unconfirmed hostname `.ahrefs.com` or published list | [AhrefsBot](robots/ahrefsbot.md), [AhrefsSiteAudit](robots/ahrefssiteaudit.md) |
| Alexa | `alexa site audit` | unconfirmed hostname `.alexa.com` | [alexa site audit](robots/alexa-site-audit.md) |
| AliyunSecBot | `AliyunSecBot` | inline range `8.217.0.0/16` | [AliyunSecBot](robots/aliyunsecbot.md) |
| Amazon Quick | `amazon-Quick-on-behalf-of` | published list (`amazon-quick-ips.json`, copied by hand) | [amazon-Quick-on-behalf-of](robots/amazon-quick-on-behalf-of.md) |
| Amazon SearchBot | `Amzn-SearchBot` | unconfirmed hostname `.crawl.amazonbot.amazon` or published list (copied by hand) | [Amzn-SearchBot](robots/amzn-searchbot.md) |
| Amazon User | `Amzn-User` | unconfirmed hostname `.crawl.amazonbot.amazon` or published list (copied by hand) | [Amzn-User](robots/amzn-user.md) |
| Amazonbot | `Amazonbot` | unconfirmed hostname `.crawl.amazonbot.amazon` or published list (copied by hand) | [Amazonbot](robots/amazonbot.md) |
| Applebot | `Applebot` | unconfirmed hostname `.apple.com` or published list | [Applebot](robots/applebot.md) |
| Aranet | `Aranet-SearchBot` | cloud hostname `.googleusercontent.com` | [Aranet-SearchBot](robots/aranet-searchbot.md) |
| Archive.org | `archive.org bot`, `special archiver`; hostname only `.us.archive.org` | unconfirmed hostname `.archive.org` | [archive.org_bot](robots/archive.org_bot.md) |
| Arquivo | `arquivo-web-crawler`, `Arquivo-web-crawler` | unconfirmed hostname `.arquivo.pt` or published list | [Arquivo-web-crawler](robots/arquivo-web-crawler.md) |
| Babbar | `Barkrowler` | unconfirmed hostname `.babbar.eu` or published list | [Barkrowler](robots/barkrowler.md) |
| Baidu | `Baiduspider`, `Baiduspider-render`, `Baiduspider-image` | unconfirmed hostname `.baidu.com` | [Baiduspider](robots/baiduspider.md) |
| Bing | `BingBot`, `BingPreview`; hostname only `.search.msn.com` | unconfirmed hostname `.search.msn.com` or published list | [bingbot](robots/bingbot.md) |
| Bluechip Backlinks | `BluechipBacklinks` | unconfirmed hostname `.bluechipbacklinks.com` | [BluechipBacklinks](robots/bluechipbacklinks.md) |
| BnF.fr | `bnf.fr bot` | unconfirmed hostname `.bnf.fr` | [bnf.fr_bot](robots/bnf.fr_bot.md) |
| British Library | `bl.uk ldfc bot`, `bl.uk lddc bot` | unconfirmed hostname `.bl.uk` | [bl.uk_lddc_bot](robots/bl.uk_lddc_bot.md) |
| Bytespider | `Bytespider` | unconfirmed hostname `.crawl.bytedance.com` or cloud hostname `.ap-southeast-1.compute.amazonaws.com` | [Bytespider](robots/bytespider.md) |
| ChatGPT | `ChatGPT-User` | published list | [ChatGPT-User](robots/chatgpt-user.md) |
| Claude | `ClaudeBot`, `Claude-User`, `Claude-SearchBot`, `Claude-Web`, `anthropic-ai` | published list | [ClaudeBot](robots/claudebot.md), [Claude-User](robots/claude-user.md), [Claude-SearchBot](robots/claude-searchbot.md) |
| Cliqz | `Cliqzbot` | cloud hostname `.eu-central-1.compute.amazonaws.com` | [Cliqzbot](robots/cliqzbot.md) |
| Coc Coc | `Coc Coc Bot`, `Coc Coc Bot Web`, `Coc Coc Bot Image`, `coccocbot-fast`, `coccocbot-ads`, `coccocbot-shopping` | unconfirmed hostname `.coccoc.com` | [coccocbot](robots/coccocbot.md) |
| Common Crawl | `CCBot` | published list | [CCBot](robots/ccbot.md) |
| DataForSeo | `DataForSeoBot` | unconfirmed hostname `.dataforseo.com` | [DataForSeoBot](robots/dataforseobot.md) |
| Daum | `Daum` | published list (`daumbot-ips.json`, copied by hand) | [Daum](robots/daum.md) |
| Discord | `Discordbot` | cloud hostname `.googleusercontent.com` or published list | [Discordbot](robots/discordbot.md) |
| Dolfe | `DolfeEngineCrawler` | cloud hostname `.googleusercontent.com` | [DolfeEngineCrawler](robots/dolfeenginecrawler.md) |
| DuckDuckGo | `DuckDuckGo`, `DuckDuckBot`, `DuckDuckBot-Https`, `DuckAssistBot`, `DuckDuckGo-Favicons-Bot` | unconfirmed hostname `.duckduckgo.com` or published lists (DuckDuckBot's and DuckAssistBot's) | [DuckDuckBot](robots/duckduckbot.md), [DuckAssistBot](robots/duckassistbot.md) |
| Exa | `ExaSearchBot` | header `signature-agent` contains `https://crawler.exa.ai` | [ExaSearchBot](robots/exasearchbot.md) |
| Facebook | `FacebookBot` | unconfirmed hostname `.fbsv.net` or published list (`meta-ips.json`) | [facebookexternalhit](robots/facebookexternalhit.md) |
| Flipboard | `FlipboardProxy` | unconfirmed hostname `.flipboard.com` | [FlipboardProxy](robots/flipboardproxy.md) |
| GitHub Camo | `github-camo` | published list (`github-ips.json`) or inline range `9.234.0.0/17` | [github-camo](robots/github-camo.md) |
| Google | `Google`, `GoogleDocs`, `docs.google.com`, `Google Favicon`, `GoogleImageProxy` | unconfirmed hostname `.google.com` | [Google Favicon](robots/google-favicon.md), [GoogleDocs](robots/googledocs.md), [GoogleImageProxy](robots/googleimageproxy.md) |
| Googlebot | `Googlebot`, `Googlebot-Image`, `Googlebot-Video`; hostname only `.googlebot.com` | unconfirmed hostname `.googlebot.com` or published list | [Googlebot](robots/googlebot.md) |
| HaloScan | `HaloBot` | published list (read from a table on its crawler page) | [HaloBot](robots/halobot.md) |
| Happy Apps | `HappyApps-WebCheck` | cloud hostname `.compute-1.amazonaws.com` | [HappyApps-WebCheck](robots/happyapps-webcheck.md) |
| Headline | `ev-crawler` | unconfirmed hostname `.headline.com` | [ev-crawler](robots/ev-crawler.md) |
| HubSpot | `HubSpot Crawler` | published list (the `WEB_SCRAPING` ranges of its network origins API) | [HubSpot Crawler](robots/hubspot-crawler.md) |
| ibou | `ibou-search`, `IbouBot` | forward-confirmed hostname `.ibou.io` or published list (one per family) | [ibou-search](robots/ibou-search.md), [IbouBot](robots/iboubot.md); `IbouBot`'s user agent parses as `www.ibou.com` (fixed in `@hyperwatch/useragent` [#227](https://github.com/hyperwatch/useragent/pull/227), not released) |
| Idarus | `IdarusBot` | inline range `141.94.42.166/32` | [IdarusBot](robots/idarusbot.md) |
| InfoTiger | `InfoTigerBot` | unconfirmed hostname `.infotiger.com` | [InfoTigerBot](robots/infotigerbot.md) |
| Keenable | `KeenableBot`, `Keenable-User` | published lists | [KeenableBot](robots/keenablebot.md), [Keenable-User](robots/keenable-user.md) |
| Line | `Linespider` | unconfirmed hostname `.search.line-apps.com` | [Linespider](robots/linespider.md) |
| LinkedIn | `LinkedInBot` | unconfirmed hostname `.linkedin.com` | [LinkedInBot](robots/linkedinbot.md) |
| Linkup | `LinkupBot` | inline range `35.198.113.100/32` | [LinkupBot](robots/linkupbot.md) |
| Lyrenth | `AIWebIndex`, `AIWebIndex-Agent` | unconfirmed hostname `.lyrenth.com` or published list | [AIWebIndex](robots/aiwebindex.md) |
| Mail.RU | `Mail.RU Bot`, `Mail.RU Bot Img`, `Mail.RU Bot Fast`, `Mail.RU Bot Robots` | unconfirmed hostname `.go.mail.ru` | [Mail.RU_Bot](robots/mail.ru_bot.md) |
| Majestic | `MJ12bot`; signature `3d36aa5118581a33dd2704f3b0c22a0b` | unconfirmed hostname `.mj12bot.com` or signature | [MJ12bot](robots/mj12bot.md) |
| MegaIndex.ru | `MegaIndex.ru` | cloud hostname `.clients.your-server.de` | [MegaIndex.ru](robots/megaindex.ru.md) |
| Meta | `meta-externalagent`, `meta-webindexer`, `Hyperlink` | published list (`meta-ips.json`) | [meta-externalagent](robots/meta-externalagent.md), [meta-webindexer](robots/meta-webindexer.md), [Hyperlink](robots/hyperlink.md) |
| Mojeek | `MojeekBot` | unconfirmed hostname `.mojeek.com` or published list | [MojeekBot](robots/mojeekbot.md) |
| Monitor Backlinks | `MBCrawler` | cloud hostname `.compute-1.amazonaws.com` | [MBCrawler](robots/mbcrawler.md) |
| Moz | `DotBot` | inline range `216.244.64.0/19` | [DotBot](robots/dotbot.md) |
| Naver | `Yeti` | unconfirmed hostname `.naver.com` or published list | [Yeti](robots/yeti.md) |
| Neevabot | `Neevabot` | unconfirmed hostname `.neevabot.com` | [Neevabot](robots/neevabot.md) |
| OpenAI GPTBot | `GPTBot` | published list | [GPTBot](robots/gptbot.md) |
| OpenAI SearchBot | `OAI-SearchBot` | published list | [OAI-SearchBot](robots/oai-searchbot.md) |
| Parallel | `ShapBot` | cloud hostname `.googleusercontent.com` or published list | [ShapBot](robots/shapbot.md) |
| Perplexity | `PerplexityBot`, `Perplexity-User` | published lists | [PerplexityBot](robots/perplexitybot.md), [Perplexity-User](robots/perplexity-user.md) |
| PetalBot | `PetalBot` | unconfirmed hostname `.petalsearch.com` | [PetalBot](robots/petalbot.md) |
| Pingdom | `PingdomBot` | unconfirmed hostname `.pingdom.com` or published list | [PingdomBot](robots/pingdombot.md) |
| Pinterest | `Pinterest`, `Pinterestbot` | unconfirmed hostname `.pinterest.com` or inline range `54.236.1.0/24` | [Pinterestbot](robots/pinterestbot.md); the parser also returns `Pinterest` for Pinterest's Android and some iOS in-app browsers |
| Qwant | `Qwantify`, `Qwantify-dev`, `Qwantbot`, `Qwantbot-news`; hostname only `.qwant.com` | unconfirmed hostname `.qwant.com` or published list | [Qwantbot](robots/qwantbot.md) |
| Raven | `Raven` | cloud hostname `.compute-1.amazonaws.com` | none matches: [RavenCrawler](robots/ravencrawler.md) parses as `RavenCrawler` |
| Reflection | `Reflectionbot` | forward-confirmed hostname `.reflection.ai` or published list | [Reflectionbot](robots/reflectionbot.md) |
| Riddler | `Riddler` | cloud hostname `.eu-west-1.compute.amazonaws.com` | [Riddler](robots/riddler.md) |
| RootCrawl | `RootCrawl`, `RootCrawl-Crawler` | unconfirmed hostname `.rootcrawl.org` or published list | [RootCrawl](robots/rootcrawl.md) |
| SE Ranking | `SERankingBacklinksBot` | unconfirmed hostname `.blex.seranking.com` or published list | [SERankingBacklinksBot](robots/serankingbacklinksbot.md) |
| Seekport | `SeekportBot`, `Seekport Crawler` | published list, or unconfirmed hostname `.007ac9.net` (`SeekportBot`), cloud hostname `.clients.your-server.de` (`Seekport Crawler`) | [SeekportBot](robots/seekportbot.md) |
| Semrush | `SemrushBot`, `SemrushBot-SWA`, `SemrushBot-OCOB`, `SemrushBot-FT`, `SemrushBot-ESI`, `SiteAuditBot`, `SplitSignalBot`, `RyteBot`; hostname only (forward-confirmed `.semrush.com`); signature `75e08e387505289898138bab5c6ee557` | forward-confirmed hostname `.semrush.com` or inline range `85.208.98.0/24` | [SemrushBot](robots/semrushbot.md), [SemrushBot-SWA](robots/semrushbot-swa.md), [SemrushBot-OCOB](robots/semrushbot-ocob.md), [SemrushBot-FT](robots/semrushbot-ft.md), [SemrushBot-ESI](robots/semrushbot-esi.md), [SiteAuditBot](robots/siteauditbot.md), [SplitSignalBot](robots/splitsignalbot.md), [RyteBot](robots/rytebot.md) |
| Sentry | `SentryUptimeBot` | cloud hostname `.googleusercontent.com` or published list | [SentryUptimeBot](robots/sentryuptimebot.md) |
| SEOkicks | `SEOkicks` | forward-confirmed hostname `.seokicks.de` | [SEOkicks](robots/seokicks.md) |
| Seznam | `SeznamBot` | unconfirmed hostname `.seznam.cz`, inline range `2a02:598::/32` or published list | [SeznamBot](robots/seznambot.md) |
| Shenma | `YisouSpider`; hostname only `.crawl.sm.cn` | unconfirmed hostname `.crawl.sm.cn` | [YisouSpider](robots/yisouspider.md) |
| Shields.io | `Shields.io` | cloud hostname `.compute-1.amazonaws.com` | [Shields.io](robots/shields.io.md) |
| Sirportly | `Sirportly t.co expander` | unconfirmed hostname `.labs.k.io` | [Sirportly](robots/sirportly.md) |
| Slack | `Slackbot-LinkExpanding` | cloud hostname `.compute-1.amazonaws.com` | [Slackbot-LinkExpanding](robots/slackbot-linkexpanding.md) |
| SleepBot | `SleepBot` | cloud hostname `.googleusercontent.com` | [SleepBot](robots/sleepbot.md) |
| Sofya | `SofyaBot` | unconfirmed hostname `.sofya.co` or published list | [SofyaBot](robots/sofyabot.md) |
| Sogou | `Sogou web spider`, `Sogou Pic Spider`; hostname only `.crawl.sogou.com` | unconfirmed hostname `.sogou.com` | [Sogou web spider](robots/sogou-web-spider.md) |
| SpiderFoot | hostname only `.hx.spiderfoot.net`; signature `6877bffcee5eb4b80f4f974d7697e809` | unconfirmed hostname or signature | [SpiderFoot](robots/spiderfoot.md) |
| Stripe | `Stripe`, `Stripebot` | unconfirmed hostname `.stripe.com` | [Stripebot](robots/stripebot.md); `Stripe` is Stripe's webhooks, not a robot |
| TikTok | `TikTokSpider` | unconfirmed hostname `.crawl.bytedance.com` or cloud hostname `.ap-southeast-1.compute.amazonaws.com` | [TikTokSpider](robots/tiktokspider.md) |
| Twitter | `Twitterbot` | unconfirmed hostname `.twttr.com` or inline ranges (X's three: `199.16.156.0/22`, `199.59.148.0/22`, `192.133.76.0/22`) | [Twitterbot](robots/twitterbot.md) |
| Ubermetrics | `Ubermetrics` | cloud hostname `.your-server.de` | [um-LN](robots/um-ln.md) |
| Uptime Robot | `UptimeRobot` | unconfirmed hostname `.uptimerobot.com` or published list | [UptimeRobot](robots/uptimerobot.md) |
| Velen | `VelenPublicWebCrawler` | cloud hostname `.googleusercontent.com` | [VelenPublicWebCrawler](robots/velenpublicwebcrawler.md) |
| WebMeUp | `AwarioBot`, `BLEXBot` | unconfirmed hostname `.webmeup.com` | [AwarioBot](robots/awariobot.md), [BLEXBot](robots/blexbot.md) |
| Wise | `TransferWise-Webhook` | cloud hostname `.eu-central-1.compute.amazonaws.com` | - (webhooks, not a robot) |
| Yahoo | `Yahoo`, `Yahoo! Slurp`, `YahooMailProxy` | unconfirmed hostname `.crawl.yahoo.net` (`Yahoo`, `Yahoo! Slurp`), `.yahoo.net` (`YahooMailProxy`) | [Slurp](robots/slurp.md), [YahooMailProxy](robots/yahoomailproxy.md) (old user agent only) |
| Yandex | `YandexBot`, `YandexImages`, `YandexMobileBot`, `YandexAccessibilityBot` | unconfirmed hostname `.yandex.com` | [YandexBot](robots/yandexbot.md) |
| You.com | `YouBot` | unconfirmed hostname `.search.you.com` or inline range `68.67.112.0/24` | [YouBot](robots/youbot.md) |
