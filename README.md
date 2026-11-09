# Touchline Atlas forecast ledger

Public copy of every forecast locked on [thetouchlineatlas.com](https://thetouchlineatlas.com/). Each forecast is a set of 1X2 probabilities from our statistical model, locked before kickoff (normally 24 hours before) and graded on the 90-minute result. Misses stay on the record.

This repository is updated automatically after each hourly batch that locks or grades a forecast. The `main` branch does not allow force pushes or deletion, so its history can only grow: the commit in which a record first appears shows when it was published here.

## Files

| File | What it holds |
|---|---|
| `records/` | One JSON file per locked forecast (`<fixture>-r<revision>.json`). Its SHA-256 is the hash shown on the match page. |
| `ledger.json` | Every locked forecast with its probabilities, hash, commit, status and, once graded, the 90-minute result and RPS. |
| `ledger.csv` | The same as a table. |
| `SHA256SUMS` | SHA-256 of `ledger.csv`, `ledger.json` and every file in `records/`. |

## Check that a forecast was not changed

1. On the match page, note the SHA-256 and the commit of the locked forecast.
2. Download `records/<fixture>-r<revision>.json` from this repository at that commit.
3. Compute its SHA-256 (`sha256sum <file>` on Linux, `shasum -a 256 <file>` on macOS, `Get-FileHash <file>` in PowerShell). It must match the hash on the match page.

To check every file at once: `sha256sum -c SHA256SUMS`.

## Licence

CC BY 4.0: reuse freely, including commercially, with credit to Touchline Atlas and a link to <https://thetouchlineatlas.com/ledger/>.

Exception: the fields `record.inputs.p_market` and `record.inputs.market` (market consensus saved at lock) are derived from third-party betting-market prices. They are stored so each hash can be checked, but they are not covered by CC BY 4.0.

For information and entertainment only. Not betting advice. 18+.
