# Security policy

This policy covers every SetOff repository without its own. Report
vulnerabilities privately through the **Security → Report a vulnerability** tab
of the affected repository, never in a public issue. We aim to acknowledge
reports within three days.

In scope, most severe first:

1. Withdrawing more than your available balance, or moving another member's funds.
2. Recording an obligation without the debtor's authorization.
3. Leaving a net debit uncovered so that `settle` fails or a balance goes negative.
4. Blocking settlement or withdrawals for other members.

Invariants the code is written to keep, and that reports should be measured
against:

- `balance + min(position, 0) >= 0` for every member and token, always.
- The sum of positions in a window, per token, is zero.
- Token balances held by the contract equal the sum of member balances.

The contract has not been audited.
