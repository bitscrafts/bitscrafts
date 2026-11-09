### Marcelo Correa

Systems engineer — Fortaleza, Brazil (UTC−3). Thirty years in Portugal before that. I write **Rust** for
the parts that must not fail quietly: decision engines, agent runtimes, embedded firmware. Everything I
ship runs under a gate that either passes with zero warnings or does not merge.

**Open to remote Rust roles** · mvcorrea@gmail.com
**Based in Fortaleza, Brazil (UTC−3). Portuguese citizen — EU work authorisation, no sponsorship needed.**
Fluent English · Portuguese (native) · Spanish and German (elementary) · remote-first, available for occasional travel

---

#### What I build

**[laya-rs](https://github.com/bitscrafts/laya-rs)** — a decision layer that replaces LLM prose with typed answers.
An agent asks a typed question (yes/no with a probability, one of N options, or a rank) and gets a typed
answer with calibrated confidence in a single parallel pass — no text generation, no parsing.
Decisions land in an append-only `redb` ledger; the payload is route-shaped, so a graph owns every edge
and the model can only choose among ports that already exist.

`cargo xtask gate` = fmt + clippy `-D warnings` + tests, **all zero**. `unwrap`/`expect`/`panic`/
`indexing_slicing` denied; `unsafe_code` forbidden workspace-wide. Seven MCP tools over stdio.
A comparison is a `check` (exit status); only a judgement is a `decide` (model call) — and the docs
record the cases where the model was measurably wrong and the check was not.

**[pi-improved](https://github.com/bitscrafts/pi-improved)** — a 22-crate Rust agent runtime.
Four binaries (`pii`, `pii-mcp`, `pii-web`, `pii-evolve`), ~90k lines in `src`, ~2,000 tests,
a 450-line file cap and a two-tree quality gate: the gate re-exports `HEAD` with `git archive` and
runs there, because a gate can be green in a dirty tree and red in a clean one.

**[pidag](https://github.com/bitscrafts/pidag)** — spec-driven DAG orchestration for LLM workers.
A spec carries a TDD contract and runnable exit criteria; the worker implements and never commits;
the orchestrator reviews the diff and commits. Provenance stays checkable.

#### Embedded

Silicon Labs **EFR32MG24** PAC + HAL crates (`EFR32MG2X-RS`) · **ESP32-C3/C6** bare-metal with
`esp-hal`/`embassy` · RP2040 · LoRa (E22/SX1262) mesh nodes · a Rust driver for an Epson TM-T88V
receipt printer when the vendor SDK was not an option.

#### How I work

- **A gate is a boolean, not an opinion.** If it passes while the real path is broken, the check is the bug.
- **Controls are mandatory.** Every rule that skips or suppresses something gets a near-miss test that
  must still take the normal path.
- **Measure the artefact, not the claim.** Numbers in a README are measured, and the failures are
  published next to the wins.
- **Fail closed.** If the decision source is unavailable, the answer is `ask` — never `allow`.

#### Stack

Rust (tokio, rmcp, redb, serde, clap) · Python for ML · MCP · `no_std`/embedded · GitHub Actions ·
LLM harness design
