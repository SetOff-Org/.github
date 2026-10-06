<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/SetOff-Org/.github/main/assets/logo-dark.svg">
    <img src="https://raw.githubusercontent.com/SetOff-Org/.github/main/assets/logo.svg" alt="SetOff" height="64">
  </picture>
</p>

<p align="center"><b>Settle the net, not every payment. Multilateral netting for anchors, payment providers and agents on Stellar.</b></p>

Participants who owe each other all day shouldn't each pre-fund their entire
outflow. SetOff collects obligations in windows and settles only net positions.
On chain, a settlement contract guarantees settlement can never fail: a
member's net debit must always be covered by its collateral.

| Repository | Language | What it does |
|---|---|---|
| [setoff-contracts](https://github.com/SetOff-Org/setoff-contracts) | Rust / Soroban | Collateral, debtor-authorized obligations, guaranteed netted settlement |
| [setoff-engine](https://github.com/SetOff-Org/setoff-engine) | Rust | Reference netting algorithm and cross-language test vectors |
| [setoff-clearing](https://github.com/SetOff-Org/setoff-clearing) | Go | Clearing service and `setoff` CLI; an independent engine that matches every vector |

Proven on testnet: a three-party cycle of 30 XLM gross obligations settled
with nothing moving, and one participant took part with no collateral at all.

We take part in the [Stellar Wave](https://www.drips.network/wave/stellar)
program. Look for issues labeled by complexity in each repository.
