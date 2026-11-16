[![token-radar-01](https://make.fun/badge/token-radar-01.svg)](https://make.fun/bounty/token-radar-01)
[![rank](https://make.fun/badge/token-radar-01/iwandarmawan/token-radar/rank.svg)](https://make.fun/bounty/token-radar-01)
[![reward](https://make.fun/badge/token-radar-01/iwandarmawan/token-radar/reward.svg)](https://make.fun/bounty/token-radar-01)

# Token Radar

A token launch radar for [make.fun](https://make.fun/bounty/token-radar-01)'s **token-radar-01** bounty ($1,325, top 10 share it).

It reads a sealed DefiLlama snapshot of 758 protocols, finds the ones that record no token, and ranks them by an **implied value** priced from the snapshot's own live market: each protocol's category comp multiple is the median market-cap-per-TVL of the live-token protocols in that category, times TVL, adjusted for seven-day growth, how long it has run with no token, and how many chains it lives on. The dashboard shows the ranked board, a detail view for each protocol with its model breakdown and farm plan, and the live-token protocols set aside with their market caps.

## How it is made

`main.ts` (Node 22, standard library only) reads `snapshot.json`, scores every rankable pre-token protocol with the radar-2 model in `lib/model.ts`, writes `board.json` and `data.js`, copies `dashboard/` and `screenshots/`, and writes `dossier.json` with the vendored make.fun library. The dashboard is a static page with no network: search, category and chain filters, a watchlist-only toggle, sortable columns, and a detail dialog per protocol.

## Run it

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts --input ../input/snapshot.json
# writes out/board.json, out/data.js, out/dashboard/, out/screenshots/ and out/dossier.json
```

## License

MIT — see [LICENSE](LICENSE).
