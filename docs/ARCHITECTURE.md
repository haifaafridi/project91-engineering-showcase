# Project 91 — High-Level Architecture

This document summarizes the engineering ideas behind Project 91 without distributing production code, privileged account details, internal identifiers, or deployable business logic.

## Conceptual component boundaries

1. **Event observation:** Observe configured wallet events from a blockchain data provider, with health, freshness, and replay awareness.
2. **Classification:** Interpret supported on-chain activity and reject uncertain or unsupported structures.
3. **Policy:** Apply eligibility and safety checks before any downstream execution workflow.
4. **Verified chain-state observation:** Validate execution-relevant chain state rather than assuming an observed event remains actionable.
5. **Durable execution lifecycle:** Separate planning, dispatch, uncertain outcomes, and final reconciliation.
6. **Positions and exits:** Maintain consistent durable position state with an attended operator interface.
7. **Desktop integration:** Keep the Windows entry point separate from the Rust backend and confidential configuration within WSL2.

## Reliability principles

- **Fail closed on ambiguity:** unsupported layouts, incomplete state, or unclear outcomes must not be silently accepted.
- **Idempotence and duplicate suppression:** receiving an event more than once should not imply performing the action twice.
- **Authoritative persistence:** stored financial workflow records govern recovery and displayed states.
- **Clear operator visibility:** distinguish skipped, deferred, failed, pending, and reconciled states.
- **Separation of control and execution:** a UI or launcher action is not equivalent to final blockchain confirmation.

## Technology choices

| Choice | Rationale |
|---|---|
| Rust / Tokio | Typed, modular, asynchronous backend |
| SQLite | Durable local transaction and control records |
| Solana event observation | External chain activity as input to the processing pipeline |
| WSL2 / Ubuntu | Consistent Rust backend environment on Windows |
| Thin Windows launcher | Desktop-friendly entry point without moving backend authority into the launcher |

## Deliberate public omissions

This overview excludes precise transaction schemas, signing, trade-construction logic, configuration values, provider endpoints, internal file paths, infrastructure access details, and the actual source-tree implementation. These details are not required for a recruiter to evaluate the architecture and ownership of the engineering work.
