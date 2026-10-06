# Getting help

- **How much would netting save us?** `setoff net obligations.csv` answers
  locally from a CSV of who owes whom; the
  [setoff-clearing README](https://github.com/SetOff-Org/setoff-clearing#readme)
  shows the format.
- **Running a clearing service:** [`examples/setoff.toml`](https://github.com/SetOff-Org/setoff-clearing/blob/main/examples/setoff.toml)
  documents every setting, and the
  [OpenAPI description](https://github.com/SetOff-Org/setoff-clearing/blob/main/api/openapi.yaml)
  every route.
- **Settling on chain:** the [setoff-contracts README](https://github.com/SetOff-Org/setoff-contracts#readme)
  lists the contract's interface and guarantees, and
  `scripts/testnet-demo.sh` deploys a copy to testnet.
- **Implementing netting in another language:** match
  [setoff-engine's reference vectors](https://github.com/SetOff-Org/setoff-engine/blob/main/docs/vectors.md).
- **Bugs:** open one in the repository concerned with the input (obligations,
  transaction hash or contract call) and the output.
- **Ways to move funds or break settlement** are security issues: report them
  privately as described in [SECURITY.md](SECURITY.md).
