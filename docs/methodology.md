# Audit methodology

## Evidence boundary

Every finding must identify the observed behavior, reproduction path, expected invariant, actual result, and business consequence. A passing unit test is not treated as proof of a live outcome.

## Core tests

- Duplicate delivery: the same event key cannot cause a second external effect.
- Concurrent execution: many contenders produce exactly one authorized winner.
- Crash recovery: resume does not repeat a completed step or lose a pending approval.
- Authority enforcement: protected actions fail closed at the execution boundary.
- Reachable approval: every approval request can resolve or reaches a named rejection.
- Ambiguous completion: timeout and partial completion trigger reconciliation, not blind retry.
- Outcome proof: intent, attempt, external receipt, and final outcome can be reconciled.

## Severity

- Critical: credible unauthorized, irreversible, or repeated external action.
- High: likely cost, data, trust, or operational impact without a reliable recovery path.
- Medium: bounded degradation with a manual recovery path.
- Low: limited impact or defense-in-depth improvement.

## Deliverable

The diagnostic returns a concise evidence table, the highest-risk failure chain, prioritized acceptance tests, and a recommendation to repair, investigate further, or stop.

