# mcpscan: agent instructions

Read `docs/SPEC.md` and `docs/adr/` first. The spec is the source of truth.

## Rules
- Rust stable, workspace layout per the spec. `cargo clippy -- -D warnings` must pass.
- Every rule has positive **and** negative fixtures plus a `docs/rules/<ID>.md` page (what, why, how to fix, references).
- `--connect` must never invoke tools, only list them. Subprocess environments are scrubbed.
- Findings must be deterministic (stable ordering) so snapshot tests and SARIF diffs are stable.
- No network calls except to MCP servers the user explicitly asked to connect to. No telemetry.
- Every source file carries the SPDX header (`python scripts/commitguard.py --fix-headers`).
- Never commit real tokens. Fixture secrets must be obviously fake and listed in `.commitguard-allow`.

## Commands
```bash
cargo fmt --check && cargo clippy --all-targets -- -D warnings
cargo test
cargo run -p mcpscan-cli -- scan --sarif out.sarif
python scripts/commitguard.py --all
```
