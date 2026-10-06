# Contributing to SetOff

This guide applies to every SetOff repository. SetOff takes part in the
[Stellar Wave](https://www.drips.network/wave/stellar) program; Wave issues are
labeled with their complexity.

## Ground rules

- **Get assigned first.** Comment on the issue and wait for assignment.
- **One issue, one PR**, linked with `Closes #N`.
- **Money is integers.** Amounts are `i128` (Rust) or `big.Int` bounded to the
  i128 range (Go), and travel as canonical decimal strings. Never floats.
- **The engines must agree.** A change to netting lands in
  [setoff-engine](https://github.com/SetOff-Org/setoff-engine) first, with
  regenerated vectors (`UPDATE_FIXTURES=1 cargo test`), and the same vectors are
  copied to [setoff-clearing](https://github.com/SetOff-Org/setoff-clearing).
- **Contract changes keep the invariants.** `balance + min(position, 0) >= 0`
  for every member, always; positions sum to zero; and no operator action may
  trap a member's available funds. Add a test that would break if they didn't,
  and keep `src/resources.rs` passing so the largest window still settles in
  one transaction.
- **Keep the tree clean.** No notes, summaries, PR drafts or backup files; CI
  rejects the common ones.

## Checks

| Repository | Before you push |
|---|---|
| setoff-contracts | `cargo fmt --all`, `cargo clippy --workspace --all-targets -- -D warnings`, `cargo test`, `stellar contract build` |
| setoff-engine | `cargo fmt`, `cargo clippy --all-targets -- -D warnings`, `cargo test` |
| setoff-clearing | `gofmt -l .`, `go vet ./...`, `go test -race ./...`, `golangci-lint run` |

`setoff-clearing`'s OpenAPI description is checked against its routes by a
test, so a new endpoint needs an entry in `api/openapi.yaml`.

## Commit messages

[Conventional Commits](https://www.conventionalcommits.org): `feat(contract): …`,
`fix(engine): …`, `docs: …`.
