# Engineering Case Studies

These summaries are based on the project's recorded development history. They intentionally avoid confidential identifiers and internal patch instructions.

## Case study 1 — Stream replay retention during startup

**Problem:** After extended downtime, the application attempted to resume wallet-event observation from a saved position no longer available within a provider's replay window. The initial UI symptom was a generic startup failure.

**Investigation:** Runtime evidence distinguished an actual replay-position rejection from a connection timeout. The team treated persisted state as authoritative rather than assuming that restarting or advancing the cursor was harmless.

**Engineering response:** A guarded recovery method required evidence that the affected historical interval was safe to skip and that a recent replay position was actually available. The process preserved financial records and did not sign or submit a transaction.

**Lesson:** The hardest part of recovery is often **proving which state change is safe**, rather than writing the update statement.

## Case study 2 — Protocol layout drift in verified account observation

**Problem:** A strict account-state parser correctly rejected unfamiliar structure, but the official underlying protocol had evolved. The result was a safe rejection rather than an incorrect transaction.

**Investigation:** Observed account structure was compared with reviewed protocol documentation. Multiple related account types required targeted compatibility checks.

**Engineering response:** Narrow parser updates recognized documented new structure, retained rejection of unexpected unknown data, and were exercised through focused tests and read-only observation.

**Lesson:** Fail-closed parsing and forward compatibility can coexist when new structures are explicitly validated.

## Case study 3 — Transaction outcomes and reconciliation

**Problem:** User-interface feedback cannot reliably distinguish “not submitted” from “submitted but not yet confirmed.” This distinction matters when an action must not be duplicated.

**Engineering response:** Durable journals and reconciliation tracked state transitions. In a controlled live Manual Sell, the initial uncertain state was reconciled to a confirmed outcome without blind duplicate submission.

**Lesson:** Blockchain product reliability requires an explicit model of **unknown, pending, confirmed, and reconciled** outcomes.

## Case study 4 — Windows client experience over a Linux backend

**Problem:** The existing Rust runtime and its sensitive durable state lived in Ubuntu/WSL2, but the client needed a usable Windows entry point.

**Engineering response:** A thin Windows launcher operated behind a clear process/control boundary, leaving execution authority and private configuration with the backend. Build and launcher self-tests were recorded.

**Lesson:** A product-quality interface is not merely a wrapper: its trust boundaries and failure semantics are part of the architecture.
