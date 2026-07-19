# Sample findings format

This example is illustrative and does not describe a customer.

## Finding: retry can duplicate an external action

- Observed behavior: the worker times out after dispatch but before recording the receipt.
- Expected invariant: one business intent produces at most one external effect.
- Failure path: timeout is classified as failure; the job retries without reconciliation.
- Business risk: duplicate message, charge, order, or protected command.
- Evidence required: intent ID, idempotency key, dispatch receipt, retry trace, final ledger state.
- Acceptance test: forty concurrent attempts plus a crash/restart replay produce one reservation and one external receipt.
- Recommended repair: durable intent reservation, idempotent dispatch, explicit ambiguous state, and receipt reconciliation before retry.

## Decision summary

- Immediate containment: disable blind retry for ambiguous completions.
- Repair priority: high.
- Deeper audit: justified only if the workflow can create material external effects.

