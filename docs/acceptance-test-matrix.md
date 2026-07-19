# Acceptance-Test Matrix

This matrix turns common agent reliability claims into behavior that can be tested. It is a review template, not a claim that every system needs every test.

| Failure boundary | Test stimulus | Required evidence | Passing behavior |
|---|---|---|---|
| Duplicate delivery | Submit the same event key concurrently | Reservation and outcome records | One execution winner; all duplicates resolve without a second side effect |
| Crash after dispatch | Stop the worker after the external request but before local completion | External receipt plus recovery decision | Recovery identifies completed, failed, or explicitly ambiguous state; it never silently repeats |
| Checkpoint resume | Interrupt after one completed node and resume | Before/after checkpoints and transition trace | Completed work is not re-run; the workflow reaches one named terminal state |
| Approval reconnection | Disconnect and reconnect while an approval is pending | Durable intent ID and session-binding history | The valid decision resolves the original intent without executing twice |
| Unreachable approval | Trigger a protected action from a webhook or scheduled job | Origin/approval routing trace | The action reaches a resolvable interrupt or a named rejection, never an unattended wait loop |
| Runaway reasoning | Repeat a known non-terminating prompt/tool path | Turn, token, time, and tool-call budgets | The run stops at a declared limit with a reason-coded terminal outcome |
| Timeout ambiguity | Force a timeout around an external action | Request ID, provider receipt, and reconciliation record | The system does not label unknown completion as safe failure or retry without reconciliation |
| Authority enforcement | Attempt a protected action without the required grant | Policy decision and execution ledger | The action is blocked at execution, not merely warned about in the prompt |

## Evidence standard

A test passes only when the execution record proves the expected terminal behavior. A green unit test, a generated report, or an architecture diagram is not enough when the live side effect or recovery state is the real outcome.

## Safe review boundary

Initial review can use redacted traces, synthetic reproductions, or screen-shared evidence. Do not publish credentials, customer data, proprietary prompts, vulnerability details, or production logs in a GitHub issue.
