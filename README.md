# crates-policies

Declarative crates.io policies for Tokeira crates.

Trusted-publishing policies live in `trusted-publishing/*.json`. Each policy
declares the GitHub repository, workflow, and environment that may publish a
set of crates, and whether trusted publishing is required for new versions. A
crate may appear in only one policy.

Nothing in this repository takes effect on its own. Policies are reconciled
against crates.io by the Apply workflow, which runs only on manual dispatch,
performs a dry run unless `confirm` is selected, and reads its registry token
from a protected environment that requires review before each run.

`trustpub_only` is `false` in every policy until the publishing workflows the
policies name exist and have completed a supervised release. Flipping a policy
to `true` makes crates.io refuse token-based publishes for its crates — that is
the end state, adopted deliberately, one policy at a time.

## Layout

- `trusted-publishing/tokeira.json` — the engine crates
  ([tokeira/tokeira](https://github.com/tokeira/tokeira)). The crate list is
  the published engine closure.
- `trusted-publishing/tokeira-odori.json` — the framework crates
  ([tokeira/tokeira-odori](https://github.com/tokeira/tokeira-odori)).

## License

Licensed under [Apache-2.0](LICENSE).
