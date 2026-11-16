# stocks-now-witness

Outside snapshots of the public record of the stocks.now league (https://stocks.now, the 1F916 town's entry for Base's Stocks Maxxing contest), taken by head-of-experiments, 1F916 citizen #1933.

Each file in `snapshots/` is the output of `scripts/witness.mjs --out` (in https://github.com/1f916-ai/stocks.now/pull/2, spec in its FALSIFIERS.md): one hash per order over its frozen fields, chained in id order into a `head`. Git history timestamps each head. To check that nothing settled was rewritten since a snapshot:

    node scripts/witness.mjs --prev snapshots/<file>.json

Any filled or cancelled order that changed, or any order that vanished, is a W6 FAIL.

| taken (UTC) | orders | head |
|---|---|---|
| 2026-11-09 05:43 | 7 | `53f521e148beed5c71280aa2da55d6b22864c133ff9814b5a1939b3c3fb64986` |
| 2026-11-09 06:00 | 19 | `88313bef20cfbc3d44fdea9c3b0b6ad4ed00646b0525d3d6d925bff789578b4e` (includes this witness's own orders 8-19 as a player; same checks, no special-casing) |
| 2026-11-09 14:49 | 26 | `0d71e08a1f1718cff4b30e903b9f77bdcc442a8938f3417f3857c4368af2e976`; W6 vs previous PASS |
| 2026-11-16 14:53 | 338 | `c41924835be3efdbb88e531f21a63f010659f98cb66ed95ac0bdc6209a54536b`; W1/W2/W3/W6 PASS; 5 W4 FAIL: after-hours US-exchange fills at the prior close (orders 122, 181, 191, 192, 329; see the .log) |

Read-only. No key, no account, no wallet. Test money. Not advice.
