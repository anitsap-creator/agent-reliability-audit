# Agent Reliability Audit

A fixed-scope diagnostic for teams running tool-using AI agents in production.

The audit looks for four costly failure classes:

1. duplicate actions during concurrency, retry, or crash windows;
2. authority rules documented but not enforced at execution;
3. ambiguous recovery after timeout or partial completion;
4. green checks that do not prove the live outcome or ledger state.

## What the diagnostic delivers

- one 30-minute failure review;
- one replay and authority-risk assessment;
- a one-page findings report with evidence and prioritized repairs;
- a go/no-go recommendation for a deeper audit.

The standard diagnostic is **USD 500 fixed scope**, agreed before work begins. A narrower **USD 250 triage** is available when the review is limited to one failure trace and one acceptance-test recommendation. If a full audit is justified, the diagnostic fee is credited toward it. No credentials or production access are required for the initial review.

## Method

We test behavior, not architecture diagrams. The core acceptance matrix covers duplicate delivery, concurrent execution, checkpoint recovery, unreachable approvals, timeout ambiguity, and proof that a protected action reaches one named terminal state.

See the [audit methodology](docs/methodology.md), [acceptance-test matrix](docs/acceptance-test-matrix.md), and [sample findings format](docs/sample-findings.md).

## Start a conversation safely

GitHub issues are public. Do not post logs, credentials, customer data, or vulnerability details. Open a [non-sensitive review request](../../issues/new?template=reliability-review.yml), or email **anit.sap@gmail.com** with only a short, non-sensitive summary. A private evidence-transfer method is agreed before any logs are reviewed.

## Status

This is an early commercial validation project. The method is based on failure modes observed while building and testing governed agent workflows; the offer has not yet accumulated public customer case studies. Claims will be updated only when evidence supports them.
