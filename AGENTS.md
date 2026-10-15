# Agents

How to add or update robot files and the identities index. Follow it step by step, so that every
run applies the same rules and the diff shows only what changed.

## What goes where

- `robots/<name>.md`: one file per robot, named after its user agent token in lowercase
  (`robots/ahrefsbot.md`). Use [`TEMPLATE.md`](TEMPLATE.md): same front matter fields, same
  sections, same order. Variants that share a `robots.txt` token and a documentation page go in one
  file (`Baiduspider`, `Baiduspider-image`, `Baiduspider-render`). Robots with their own token get
  their own file (`Amzn-SearchBot` next to `Amazonbot`).
- [`identities.md`](identities.md): every identity Hyperwatch sets, how it is verified, and the
  robot files it covers. See [Identities index](#identities-index).
- `README.md`: the robots table, one row per file, sorted by name (case-insensitive). Update it
  whenever a file is added or its front matter changes.

A robot is anything that fetches pages on its own or on someone's behalf: crawlers, AI fetchers,
link previews, feed readers, monitoring, image proxies. Webhook senders (payment notifications)
are not robots: list them in `identities.md` only.

## Sources

1. The operator's own pages first: its bot documentation, published IP lists, `robots.txt` help.
   Fetch them; don't rely on memory. Record each URL with the date checked in "Sources".
2. Other sources (Wikipedia, articles, other bot databases) only for what the operator doesn't say,
   named as such in the text ("According to …").
3. What isn't documented says "Not documented". Never fill a gap with a guess, a typical value or
   another robot's behavior.
4. For an IP list, give its URL, format, number of prefixes and the date the list says it was
   generated, on the day you checked it. Don't copy the prefixes unless there are three or fewer.
5. A robot whose operator can't be found: `operator: Unknown`, `category: unknown`, and say what
   was searched.

## Hyperwatch section

Read Hyperwatch's source at the version named in `identities.md`, not memory:

- the agent family: parse every user agent of the file with `@hyperwatch/useragent`
  (`node -e "console.log(require('@hyperwatch/useragent').parse(process.argv[1]).family)" '<ua>'`);
- the identity rule: the `case` for that family in `src/modules/identity.js`, the "Hostname only"
  and "Signature" fallbacks at the end, and any list in `src/data/`.

Say exactly what the rule checks, in the terms below, and where it falls short of the operator's
documentation (a missing range, a hostname suffix not documented, a list not used). Read the code
carefully: `hostname` is the unconfirmed reverse DNS name, `verifiedHostname` the forward-confirmed
one. Don't call a check forward-confirmed unless it uses `verifiedHostname`.

| Term | Rule |
|---|---|
| published list | the address is in a list from `src/data/`, fetched from the operator |
| inline range | the address is in a range written in `identity.js` |
| forward-confirmed hostname | `verifiedHostname` ends with a suffix |
| unconfirmed hostname | `hostname` ends with a suffix: whoever controls the address's reverse DNS can set it |
| cloud hostname | `hostname` ends with a cloud provider's suffix (`*.compute-1.amazonaws.com`, `*.googleusercontent.com`, `*.your-server.de`): any customer of that provider passes |
| header | a request header's value, not checked cryptographically |
| signature | the request's header fingerprint (`signature.id`) |

## Observed parts

"Observed HTTP headers" and the "### Observed" part of "IP ranges and verification" come from
traffic of a site running Hyperwatch. Without access to such data, write
"No requests from this robot were captured with their headers yet." and leave out "### Observed".
Never invent observations, and never take them from another source.

With data, the rules in the README apply: no site names, no request counts (only "fewer than 10",
"dozens of", "hundreds of", "thousands of"), no client addresses, only the robot's own requests
(verified ones when Hyperwatch has an identity), no headers set by the site's own code or by the CDN
(`accept-encoding`, `if-none-match`, `if-modified-since`). Networks only when no ranges are
published; hostnames only when different from the documented ones.

## Identities index

`identities.md` lists every identity set in `src/modules/identity.js`, sorted by name:

| Column | Content |
|---|---|
| Identity | the exact string set |
| Agent families | the `case` values leading to it, and "hostname only" or "signature" fallbacks |
| Check | the terms above, joined with "or" as in the code |
| Robot files | links to the files it covers, or "-" |

Below the table, three lists:

1. **Weak checks**: identities relying on an unconfirmed hostname, a cloud hostname or an
   unchecked header, with what the operator documents that would be stronger.
2. **Missing or outdated ranges**: rules whose ranges differ from the operator's published ones.
3. **Robots without identity**: robot files with `hyperwatch.identity: null` whose operator
   publishes ranges or hostnames, i.e. could be verified.

When the identity rules change, update the version line at the top of `identities.md`, re-check
every row and every robot file's "Hyperwatch" section and `hyperwatch` front matter.

## Public repository

This repository is public. Never name the sites where traffic was observed, never give request
counts or client addresses, never include credentials or tokens.

## Commits

One commit per logical change, with a plain message saying what changed ("Add AhrefsBot, DotBot
and DataForSeoBot", "Update Twitterbot ranges"). Update `last_checked` in every file you checked.
