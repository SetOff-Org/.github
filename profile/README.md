<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/SetOff-Org/.github/main/assets/logo-dark.svg">
    <img src="https://raw.githubusercontent.com/SetOff-Org/.github/main/assets/logo.svg" alt="SetOff" height="64">
  </picture>
</p>

<p align="center"><b>Settle the net, not every payment. Multilateral netting for anchors, payment providers and agents on Stellar.</b></p>

<p align="center"><a href="https://setoff-org.github.io/setoff-engine/"><b>Simulate netting in your browser →</b></a></p>

Participants who owe each other all day shouldn't each pre-fund their entire
outflow. SetOff collects obligations in windows and settles only net positions.
On chain, a settlement contract guarantees settlement can never fail: a
member's net debit must always be covered by its collateral.

| Repository | Language | What it does |
|---|---|---|
| [setoff-contracts](https://github.com/SetOff-Org/setoff-contracts) | Rust / Soroban | Collateral, debtor-authorized obligations, guaranteed netted settlement |
| [setoff-engine](https://github.com/SetOff-Org/setoff-engine) | Rust | Reference netting algorithm, plan CSV output, and cross-language test vectors |
| [setoff-clearing](https://github.com/SetOff-Org/setoff-clearing) | Go | Clearing service and `setoff` CLI: windows, SEP-10 sign-in, camt.053 statements, on-chain settlement plans |

**From obligations to settlement:** participants post what they owe to the
clearing service (signing in with their Stellar accounts), see their own side
of the window, and the operator or a schedule closes it. `setoff soroban` turns
a closed window into the contract calls that settle it, submitting the netted
plan rather than every payment, and `setoff report` produces ISO 20022 camt.053
statements for treasury systems.

**Guarantees, tested:** randomised tests check after every step that tokens
held equal balances, positions sum to zero and every debit is covered; a
resource test keeps the largest window inside one transaction's limits; and no
operator action can trap a member's available funds.

**Proven on testnet:** a three-party cycle of 30 XLM gross obligations settled
with nothing moving, and one participant took part with no collateral at all
([contract](https://stellar.expert/explorer/testnet/contract/CCW6QCOSJTTJHDXJOVQ36NVIBAHBUVPMSZNOIJ3A444O6YMVHR4ZEYQV)).

**Contributing:** we take part in the
[Stellar Wave](https://www.drips.network/wave/stellar) program; issues are
labeled by complexity. Read [CONTRIBUTING](https://github.com/SetOff-Org/.github/blob/main/CONTRIBUTING.md)
first, and report security issues privately as described in
[SECURITY](https://github.com/SetOff-Org/.github/blob/main/SECURITY.md).
