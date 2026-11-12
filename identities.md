# Hyperwatch identities

Every identity set by Hyperwatch 5.6.0 (`src/modules/identity.js`), checked 2026-11-12: the agent
families leading to it, what is checked, and the robot files it covers. The terms in "Check" are
defined in [`AGENTS.md`](AGENTS.md#hyperwatch-section). Hostnames are patterns (`*` stands for part
of one label) or suffixes (starting with a dot). Rules apply in this order: "signed only" first (a
verified signature of one of the `signedOnly` agents, any user agent), then the rule of the agent
family, then the "hostname only" fallback, Google Special Crawlers, Google Agent and Google Proxy,
and the "signature" fallback, in that order, also for any user agent. Within a rule, checks are listed in the code's order:
hostname, then signature, then address ranges. "Published list" means a list in `src/data/` refreshed by `node scripts/fetch-ips.js`
from the sources in `src/data/ip-list-sources.json`, unless it says "copied by hand". "Verified
signature" needs the `webbotauth` module (off by default).

"Last seen" is the month of the latest request verified as the identity on a site running Hyperwatch
(see [`AGENTS.md`](AGENTS.md#last-seen)), "-" when none was seen since that site's logs start
(2026-11-09). It tracks which identities are actually seen, not why others aren't.

| Identity | Agent families | Check | Robot files | Last seen |
|---|---|---|---|---|
| 360Spider | `360Spider` | published list (`360spider-ips.json`, copied by hand) | [360Spider](robots/360spider.md) | - |
| Ahrefs | `AhrefsBot`, `AhrefsSiteAudit`, `YepBot` | forward-confirmed hostname `.ahrefs.com`, verified signature `https://ahrefs.com` or published list | [AhrefsBot](robots/ahrefsbot.md), [AhrefsSiteAudit](robots/ahrefssiteaudit.md), [YepBot](robots/yepbot.md) | 2026-11 |
| Alexa | `alexa site audit` | unconfirmed hostname `.alexa.com` | [alexa site audit](robots/alexa-site-audit.md) | - |
| AliyunSecBot | `AliyunSecBot` | inline range `8.217.0.0/16` | [AliyunSecBot](robots/aliyunsecbot.md) | - |
| Amazon Quick | `amazon-Quick-on-behalf-of` | published list (`amazon-quick-ips.json`, copied by hand) | [amazon-Quick-on-behalf-of](robots/amazon-quick-on-behalf-of.md) | 2026-11 |
| Amazon SearchBot | `Amzn-SearchBot` | forward-confirmed hostname `*.crawl.amazonbot.amazon` or published list (copied by hand) | [Amzn-SearchBot](robots/amzn-searchbot.md) | - |
| Amazon User | `Amzn-User` | forward-confirmed hostname `*.crawl.amazonbot.amazon` or published list (copied by hand) | [Amzn-User](robots/amzn-user.md) | - |
| Amazonbot | `Amazonbot` | forward-confirmed hostname `*.crawl.amazonbot.amazon` or published list (copied by hand) | [Amazonbot](robots/amazonbot.md) | 2026-11 |
| Applebot | `Applebot` | forward-confirmed hostname `*.applebot.apple.com` or published list | [Applebot](robots/applebot.md) | 2026-11 |
| Aranet | `Aranet-SearchBot` | cloud hostname `.googleusercontent.com` | [Aranet-SearchBot](robots/aranet-searchbot.md) | - |
| Archive.org | `archive.org bot`, `special archiver`; hostname only `crawl*.us.archive.org`, `wbgrp-crawl*.us.archive.org` (forward-confirmed) | forward-confirmed hostname `k8s-worker-*.ca.archive.org`, `crawl*.us.archive.org`, `wbgrp-crawl*.us.archive.org` | [archive.org_bot](robots/archive.org_bot.md) | 2026-11 |
| Arquivo | `arquivo-web-crawler`, `Arquivo-web-crawler` | forward-confirmed hostname `p*.arquivo.pt` or published list | [Arquivo-web-crawler](robots/arquivo-web-crawler.md) | - |
| Babbar | `Barkrowler` | forward-confirmed hostname `c*.babbar.eu`, verified signature `https://ibou.io` or published list | [Barkrowler](robots/barkrowler.md) | 2026-11 |
| Baidu | `Baiduspider`, `Baiduspider-render`, `Baiduspider-image` | unconfirmed hostname `baiduspider-*.crawl.baidu.com` | [Baiduspider](robots/baiduspider.md) | - |
| Bing | `BingBot`, `BingPreview`; hostname only `msnbot-*.search.msn.com` (forward-confirmed) | forward-confirmed hostname `msnbot-*.search.msn.com` or published list | [bingbot](robots/bingbot.md) | 2026-11 |
| Bluechip Backlinks | `BluechipBacklinks` | unconfirmed hostname `.bluechipbacklinks.com` | [BluechipBacklinks](robots/bluechipbacklinks.md) | - |
| BnF.fr | `bnf.fr bot` | forward-confirmed hostname `robot*-depot-legal-web.bnf.fr` | [bnf.fr_bot](robots/bnf.fr_bot.md) | 2026-11 |
| British Library | `bl.uk ldfc bot`, `bl.uk lddc bot` | unconfirmed hostname `.bl.uk` | [bl.uk_lddc_bot](robots/bl.uk_lddc_bot.md) | - |
| Bytespider | `Bytespider` | unconfirmed hostname `.crawl.bytedance.com` or cloud hostname `.ap-southeast-1.compute.amazonaws.com` | [Bytespider](robots/bytespider.md) | 2026-11 |
| ChatGPT | `ChatGPT-User` | published list | [ChatGPT-User](robots/chatgpt-user.md) | 2026-11 |
| ChatGPT Agent | signed only `https://chatgpt.com` | any user agent: verified signature `https://chatgpt.com` (a `ChatGPT-User` request with one too) | [ChatGPT Agent](robots/chatgpt-agent.md) | - |
| Claude | `ClaudeBot`, `Claude-User`, `Claude-SearchBot`, `Claude-Web`, `anthropic-ai` | published list | [ClaudeBot](robots/claudebot.md), [Claude-User](robots/claude-user.md), [Claude-SearchBot](robots/claude-searchbot.md) | 2026-11 |
| Cliqz | `Cliqzbot` | cloud hostname `.eu-central-1.compute.amazonaws.com` | [Cliqzbot](robots/cliqzbot.md) | - |
| Coc Coc | `Coc Coc Bot`, `Coc Coc Bot Web`, `Coc Coc Bot Image`, `coccocbot-fast`, `coccocbot-ads`, `coccocbot-shopping`; hostname only `bot-*.coccoc.com` (forward-confirmed) | forward-confirmed hostname `bot-*.coccoc.com` | [coccocbot](robots/coccocbot.md) | 2026-11 |
| Common Crawl | `CCBot` | published list | [CCBot](robots/ccbot.md) | 2026-11 |
| DataForSeo | `DataForSeoBot` | forward-confirmed hostname `crawling-gateway-*.dataforseo.com` or published list (`dataforseo-ips.json`, copied by hand) | [DataForSeoBot](robots/dataforseobot.md) | 2026-11 |
| Daum | `Daum` | published list (`daumbot-ips.json`, copied by hand) | [Daum](robots/daum.md) | - |
| Discord | `Discordbot` | cloud hostname `.googleusercontent.com` or published list | [Discordbot](robots/discordbot.md) | 2026-11 |
| Dolfe | `DolfeEngineCrawler` | cloud hostname `.googleusercontent.com` | [DolfeEngineCrawler](robots/dolfeenginecrawler.md) | - |
| DuckDuckGo | `DuckDuckGo`, `DuckDuckBot`, `DuckDuckBot-Https`, `DuckAssistBot`, `DuckDuckGo-Favicons-Bot`; signed only `https://bot.duckduckgo.com` | forward-confirmed hostname `*.crawl.duckduckgo.com`, verified signature `https://assistbot.duckduckgo.com` or published lists (DuckDuckBot's and DuckAssistBot's); any user agent: verified signature `https://bot.duckduckgo.com` | [DuckDuckBot](robots/duckduckbot.md), [DuckAssistBot](robots/duckassistbot.md) | 2026-11 |
| Exa | `ExaSearchBot`, `ExaSearchBot-Images`; signed only `https://exauser.crawler.exa.ai` | with the `webbotauth` module, verified signature `https://crawler.exa.ai` (`ExaSearchBot`), `https://images.crawler.exa.ai` (`ExaSearchBot-Images`); without it, header `signature-agent` contains `"https://crawler.exa.ai"` or `"https://images.crawler.exa.ai"`; any user agent: verified signature `https://exauser.crawler.exa.ai` | [ExaSearchBot](robots/exasearchbot.md), [ExaSearchBot-Images](robots/exasearchbot-images.md), [ExaUser](robots/exauser.md) | 2026-11 |
| Facebook | `FacebookBot` | forward-confirmed hostname `fwdproxy-*.fbsv.net` or published list (`meta-ips.json`) | [facebookexternalhit](robots/facebookexternalhit.md) | 2026-11 |
| Flipboard | `FlipboardProxy` | forward-confirmed hostname `*.proxy.flipboard.com` | [FlipboardProxy](robots/flipboardproxy.md) | 2026-11 |
| GitHub Camo | `github-camo` | published list (`github-ips.json`) or inline range `9.234.0.0/17` | [github-camo](robots/github-camo.md) | 2026-11 |
| Google Agent | signed only `https://agent.bot.goog`; any user agent (after "hostname only") | verified signature `https://agent.bot.goog` (keys found by the directory's `kid`), before the family rules; otherwise published list (`google-user-triggered-agents-ips.json`, Google-Agent's `user-triggered-agents.json`), checked after Google Special Crawlers | [Google-Agent](robots/google-agent.md) | 2026-11 |
| Google Proxy | `Google`, `GoogleDocs`, `docs.google.com`, `Google Favicon`, `GoogleImageProxy`; any user agent (after "hostname only") | published list (`google-user-triggered-fetchers-google-ips.json`, Google's own user-triggered fetchers) or forward-confirmed hostname `google-proxy-*.google.com`; checked after Google Special Crawlers and Google Agent | [Google Favicon](robots/google-favicon.md), [GoogleDocs](robots/googledocs.md), [GoogleImageProxy](robots/googleimageproxy.md), [GooglePlusBot](robots/googleplusbot.md) | 2026-11 |
| Google Special Crawlers | `Google`, `GoogleDocs`, `docs.google.com`, `Google Favicon`, `GoogleImageProxy`; any user agent (after "hostname only") | published list (`google-special-crawlers-ips.json`) or forward-confirmed hostname `rate-limited-proxy-*.google.com` | [AdsBot-Google](robots/adsbot-google.md) | 2026-11 |
| Googlebot | `Googlebot`, `Googlebot-Image`, `Googlebot-Video`; hostname only `crawl-*.googlebot.com`, `geo-crawl-*.geo.googlebot.com` (forward-confirmed) | forward-confirmed hostname `crawl-*.googlebot.com`, `geo-crawl-*.geo.googlebot.com` or published list | [Googlebot](robots/googlebot.md) | 2026-11 |
| HaloScan | `HaloBot` | published list (read from a table on its crawler page) | [HaloBot](robots/halobot.md) | 2026-11 |
| Happy Apps | `HappyApps-WebCheck` | cloud hostname `.compute-1.amazonaws.com` | [HappyApps-WebCheck](robots/happyapps-webcheck.md) | - |
| Headline | `ev-crawler` | forward-confirmed hostname `*.core.headline.com` | [ev-crawler](robots/ev-crawler.md) | 2026-11 |
| HubSpot | `HubSpot Crawler` | published list (the `WEB_SCRAPING` ranges of its network origins API) | [HubSpot Crawler](robots/hubspot-crawler.md) | - |
| ibou | `ibou-search`, `IbouBot` | forward-confirmed hostname `.ibou.io`, verified signature `https://ibou.io` (`ibou-search` only) or published list (one per family) | [ibou-search](robots/ibou-search.md), [IbouBot](robots/iboubot.md) | 2026-11 |
| Idarus | `IdarusBot` | inline range `141.94.42.166/32` | [IdarusBot](robots/idarusbot.md) | - |
| InfoTiger | `InfoTigerBot` | unconfirmed hostname `.infotiger.com` | [InfoTigerBot](robots/infotigerbot.md) | - |
| Ison | signed only `https://search.isonai.com` | any user agent: verified signature `https://search.isonai.com`; the published list is not used | [IsonSearchBot](robots/isonsearchbot.md) | - |
| Kakao | `KakaoBot` | published list (`kakaobot-ips.json`, read from Kakao's HTML help page) | [KakaoBot](robots/kakaobot.md) | - |
| Keenable | `KeenableBot`, `Keenable-User` | verified signatures (`https://keenablebot.keenable.ai`, `https://keenable-user.keenable.ai`) or published lists | [KeenableBot](robots/keenablebot.md), [Keenable-User](robots/keenable-user.md) | - |
| Line | `Linespider` | unconfirmed hostname `.search.line-apps.com` | [Linespider](robots/linespider.md) | - |
| LinkChecker | `LinkCheckerBot` | published list (`linkcheckerbot-ips.json`) | [LinkCheckerBot](robots/linkcheckerbot.md) | 2026-11 |
| LinkedIn | `LinkedInBot` | forward-confirmed hostname `*.fwd.linkedin.com` | [LinkedInBot](robots/linkedinbot.md) | 2026-11 |
| Linkup | `LinkupBot` | published list (`linkupbot-ips.json`) | [LinkupBot](robots/linkupbot.md) | 2026-11 |
| Lyrenth | `AIWebIndex`, `AIWebIndex-Agent`; hostname only `crawler-*.lyrenth.com`, `render-*.lyrenth.com` (forward-confirmed) | forward-confirmed hostname `crawler-*.lyrenth.com`, `render-*.lyrenth.com`, verified signature `https://api.lyrenth.com` or published list | [AIWebIndex](robots/aiwebindex.md) | 2026-11 |
| Mail.RU | `Mail.RU Bot`, `Mail.RU Bot Img`, `Mail.RU Bot Fast`, `Mail.RU Bot Robots` | unconfirmed hostname `.go.mail.ru` | [Mail.RU_Bot](robots/mail.ru_bot.md) | - |
| Majestic | `MJ12bot`; signature `3d36aa5118581a33dd2704f3b0c22a0b` | forward-confirmed hostname `crawl-*.mj12bot.com` or signature | [MJ12bot](robots/mj12bot.md) | 2026-11 |
| MegaIndex.ru | `MegaIndex.ru` | cloud hostname `.clients.your-server.de` | [MegaIndex.ru](robots/megaindex.ru.md) | - |
| Meta | `meta-externalagent`, `meta-webindexer`, `Hyperlink` | published list (`meta-ips.json`) | [meta-externalagent](robots/meta-externalagent.md), [meta-webindexer](robots/meta-webindexer.md), [Hyperlink](robots/hyperlink.md) | 2026-11 |
| Mojeek | `MojeekBot` | forward-confirmed hostname `crawl-*.mojeek.com` or published list | [MojeekBot](robots/mojeekbot.md) | - |
| Monitor Backlinks | `MBCrawler` | cloud hostname `.compute-1.amazonaws.com` | [MBCrawler](robots/mbcrawler.md) | - |
| Moz | `DotBot` | inline range `216.244.64.0/19` | [DotBot](robots/dotbot.md) | 2026-11 |
| Naver | `Yeti`; hostname only `crawl.*.web.naver.com` (forward-confirmed) | forward-confirmed hostname `crawl.*.web.naver.com`, verified signature `https://bot.naver.com` or published list | [Yeti](robots/yeti.md) | 2026-11 |
| Neevabot | `Neevabot` | unconfirmed hostname `.neevabot.com` | [Neevabot](robots/neevabot.md) | - |
| NICT | `ICC-Crawler` | inline ranges (NICT's two addresses: `202.180.34.186/32`, `61.86.246.72/32`) | [ICC-Crawler](robots/icc-crawler.md) | 2026-11 |
| Octen | signed only `https://crawler.octen.ai` | any user agent: verified signature `https://crawler.octen.ai` | [OctenSearchBot](robots/octensearchbot.md) | - |
| OpenAI GPTBot | `GPTBot` | published list | [GPTBot](robots/gptbot.md) | 2026-11 |
| OpenAI SearchBot | `OAI-SearchBot` | published list | [OAI-SearchBot](robots/oai-searchbot.md) | 2026-11 |
| Parallel | `ShapBot`; signed only `https://shap-user.parallel.ai` | cloud hostname `.googleusercontent.com`, verified signature `https://shapbot.parallel.ai` or published list; any user agent: verified signature `https://shap-user.parallel.ai` | [ShapBot](robots/shapbot.md), [Shap-User](robots/shap-user.md) | 2026-11 |
| PayPal | `PayPal`, `PayPal IPN` | forward-confirmed hostname `.paypal.com` | - (notifications, not a robot) | 2026-11 |
| Perplexity | `PerplexityBot`, `Perplexity-User` | published lists | [PerplexityBot](robots/perplexitybot.md), [Perplexity-User](robots/perplexity-user.md) | 2026-11 |
| PetalBot | `PetalBot` | forward-confirmed hostname `petalbot-*.petalsearch.com` | [PetalBot](robots/petalbot.md) | 2026-11 |
| Pingdom | `PingdomBot` | forward-confirmed hostname `s*.pingdom.com` or published list | [PingdomBot](robots/pingdombot.md) | 2026-11 |
| Pinterest | `Pinterest`, `Pinterestbot` | forward-confirmed hostname `crawl-*.pinterest.com` or inline range `54.236.1.0/24` | [Pinterestbot](robots/pinterestbot.md); the parser also returns `Pinterest` for Pinterest's Android and some iOS in-app browsers | - |
| PostHog | signed only `https://us.posthog.com` | any user agent: verified signature `https://us.posthog.com` | [PostHogImageFetcherBot](robots/posthogimagefetcherbot.md) | - |
| Qwant | `Qwantify`, `Qwantify-dev`, `Qwantbot`, `Qwantbot-news`; hostname only `qwantbot-*.qwant.com` (forward-confirmed) | forward-confirmed hostname `qwantbot-*.qwant.com` or published list | [Qwantbot](robots/qwantbot.md) | 2026-11 |
| Raven | `Raven` | cloud hostname `.compute-1.amazonaws.com` | none matches: [RavenCrawler](robots/ravencrawler.md) parses as `RavenCrawler` | - |
| Reflection | `Reflectionbot` | forward-confirmed hostname `.reflection.ai` or published list | [Reflectionbot](robots/reflectionbot.md) | 2026-11 |
| Riddler | `Riddler` | cloud hostname `.eu-west-1.compute.amazonaws.com` | [Riddler](robots/riddler.md) | - |
| River | `RiverBot` | forward-confirmed hostname `.bot.river.ai`, verified signature `https://river.ai` or published list | [RiverBot](robots/riverbot.md) | - |
| RootCrawl | `RootCrawl`, `RootCrawl-Crawler` | forward-confirmed hostname `.rootcrawl.org`, verified signature `https://rootcrawl.org` or published list | [RootCrawl](robots/rootcrawl.md) | - |
| SE Ranking | `SERankingBacklinksBot` | forward-confirmed hostname `discovery-crawler*.blex.seranking.com` or published list | [SERankingBacklinksBot](robots/serankingbacklinksbot.md) | 2026-11 |
| Seekport | `SeekportBot`, `Seekport Crawler` | published list, or forward-confirmed hostname `.007ac9.net` (`SeekportBot`), cloud hostname `.clients.your-server.de` (`Seekport Crawler`) | [SeekportBot](robots/seekportbot.md) | - |
| Semrush | `SemrushBot`, `SemrushBot-SWA`, `SemrushBot-OCOB`, `SemrushBot-FT`, `SemrushBot-ESI`, `SiteAuditBot`, `SplitSignalBot`, `RyteBot`; hostname only (forward-confirmed `.semrush.com`); signature `75e08e387505289898138bab5c6ee557` | forward-confirmed hostname `.semrush.com` or inline range `85.208.98.0/24` | [SemrushBot](robots/semrushbot.md), [SemrushBot-SWA](robots/semrushbot-swa.md), [SemrushBot-OCOB](robots/semrushbot-ocob.md), [SemrushBot-FT](robots/semrushbot-ft.md), [SemrushBot-ESI](robots/semrushbot-esi.md), [SiteAuditBot](robots/siteauditbot.md), [SplitSignalBot](robots/splitsignalbot.md), [RyteBot](robots/rytebot.md) | 2026-11 |
| Sentry | `SentryUptimeBot` | cloud hostname `.googleusercontent.com` or published list | [SentryUptimeBot](robots/sentryuptimebot.md) | 2026-11 |
| SEOkicks | `SEOkicks` | forward-confirmed hostname `.seokicks.de` | [SEOkicks](robots/seokicks.md) | - |
| Seznam | `SeznamBot` | forward-confirmed hostname `fulltextrobot-*.seznam.cz`, inline range `2a02:598::/32` or published list | [SeznamBot](robots/seznambot.md) | 2026-11 |
| Shenma | `YisouSpider`; hostname only `.crawl.sm.cn` | unconfirmed hostname `.crawl.sm.cn` | [YisouSpider](robots/yisouspider.md) | - |
| Shields.io | `Shields.io` | cloud hostname `.compute-1.amazonaws.com` | [Shields.io](robots/shields.io.md) | - |
| Sirportly | `Sirportly t.co expander` | unconfirmed hostname `.labs.k.io` | [Sirportly](robots/sirportly.md) | - |
| Slack | `Slackbot-LinkExpanding` | cloud hostname `.compute-1.amazonaws.com` | [Slackbot-LinkExpanding](robots/slackbot-linkexpanding.md) | 2026-11 |
| SleepBot | `SleepBot` | cloud hostname `.googleusercontent.com` | [SleepBot](robots/sleepbot.md) | - |
| Sofya | `SofyaBot` | forward-confirmed hostname `crawl-*.sofya.co` or published list | [SofyaBot](robots/sofyabot.md) | 2026-11 |
| Sogou | `Sogou web spider`, `Sogou Pic Spider`; hostname only `sogouspider-*.crawl.sogou.com` (forward-confirmed) | forward-confirmed hostname `sogouspider-*.crawl.sogou.com` | [Sogou web spider](robots/sogou-web-spider.md) | - |
| SpiderFoot | hostname only `.hx.spiderfoot.net`; signature `6877bffcee5eb4b80f4f974d7697e809` | unconfirmed hostname or signature | [SpiderFoot](robots/spiderfoot.md) | - |
| Stripe | `Stripe`, `Stripebot`; hostname only `crawl.stripe.com`, `*.crawl.stripe.com`, `ip-*.stripe.com` (forward-confirmed) | forward-confirmed hostname `crawl.stripe.com`, `*.crawl.stripe.com`, `ip-*.stripe.com` | [Stripebot](robots/stripebot.md); `Stripe` is Stripe's webhooks, not a robot | 2026-11 |
| Substack | signed only `https://substack.com` | any user agent: verified signature `https://substack.com` | [SubstackContentFetch](robots/substackcontentfetch.md) | - |
| TikTok | `TikTokSpider` | unconfirmed hostname `.crawl.bytedance.com` or cloud hostname `.ap-southeast-1.compute.amazonaws.com` | [TikTokSpider](robots/tiktokspider.md) | 2026-11 |
| Twitter | `Twitterbot` | forward-confirmed hostname `r-*.twttr.com` or inline ranges (X's three: `199.16.156.0/22`, `199.59.148.0/22`, `192.133.76.0/22`) | [Twitterbot](robots/twitterbot.md) | 2026-11 |
| Ubermetrics | `Ubermetrics` | cloud hostname `.your-server.de` | [um-LN](robots/um-ln.md) | - |
| Uptime Robot | `UptimeRobot` | forward-confirmed hostname `checker-*.uptimerobot.com` or published list | [UptimeRobot](robots/uptimerobot.md) | 2026-11 |
| Velen | `VelenPublicWebCrawler` | cloud hostname `.googleusercontent.com` | [VelenPublicWebCrawler](robots/velenpublicwebcrawler.md) | - |
| WebMeUp | `AwarioBot`, `BLEXBot` | forward-confirmed hostname `pot*.webmeup.com` | [AwarioBot](robots/awariobot.md), [BLEXBot](robots/blexbot.md) | - |
| Wise | `TransferWise-Webhook` | cloud hostname `.eu-central-1.compute.amazonaws.com` | - (webhooks, not a robot) | 2026-11 |
| Yahoo | `Yahoo`, `Yahoo! Slurp`, `YahooMailProxy` | unconfirmed hostname `.crawl.yahoo.net` (`Yahoo`, `Yahoo! Slurp`), `.yahoo.net` (`YahooMailProxy`) | [Slurp](robots/slurp.md), [YahooMailProxy](robots/yahoomailproxy.md) (old user agent only) | - |
| Yandex | `YandexBot`, `YandexImages`, `YandexMobileBot`, `YandexAccessibilityBot`; hostname only `*.spider.yandex.com` (forward-confirmed) | forward-confirmed hostname `*.spider.yandex.com` | [YandexBot](robots/yandexbot.md) | 2026-11 |
| You.com | `YouBot`; hostname only `youbot-*.search.you.com` (forward-confirmed) | forward-confirmed hostname `youbot-*.search.you.com`, verified signature `https://you.com` or inline range `68.67.112.0/24` | [YouBot](robots/youbot.md) | 2026-11 |
