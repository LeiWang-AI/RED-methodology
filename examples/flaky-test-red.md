# Case study: Fixing a flaky Jest test with RED (verification-gated decomposition)

Created: 2026-01-17
Updated: 2026-01-17

This is a public-facing, anonymized version of an internal debugging case study.

Goal: Show how RED (Recursive Execution Decomposition) finds the real cause of a flaky test by forcing explicit hypotheses, verification steps, and contract checks.

---

## 1) The bug (plain English)
A test sometimes passed when run alone but failed when run as part of the full test suite.

Symptom:
- Test 'should write to file when outputPath provided' failed with 'Invalid registry structure' in the full suite.
- The same test passed in isolation.

After an initial fix attempt, a second test began failing with the same error.

---

## 2) Why flakiness is dangerous
Flaky tests cause:
- loss of trust in CI
- wasted time rerunning pipelines
- real regressions getting ignored

A key RED principle: treat flakiness as a signal of hidden state, hidden assumptions, or contract violations.

---

## 3) Root cause (what actually happened)
There were two coupled issues:

1) Contract violation
A test passed invalid input ('{}' which parses to {}) into a function that requires fields like version, last_updated, and categories. The function correctly threw Error('Invalid registry structure').

2) Unhandled async
The test created a Promise that rejected, but it did not await it. That unhandled rejection leaked into later tests, creating nondeterministic behavior that depended on suite execution order.

---

## 4) The RED approach (what changed)
Instead of asking 'why is this validation failing?', RED reframed the problem as:

> What are all plausible causes of a flaky test (passes alone, fails in suite), and which cause survives verification?

RED forces a branch-and-verify workflow:
- enumerate causes
- falsify branches quickly
- drill down only on the branch that still explains the observed behavior

---

## 5) RED decomposition (abridged)

### Level 1: enumerate plausible causes
- non-determinism in implementation
- shared mutable state between tests
- execution order dependency
- async operations not awaited

Triage result: async-not-awaited is high probability, so drill down first.

### Level 2: verify async-not-awaited
- identify the promise
- check whether the test is async
- confirm the promise can reject
- confirm it is not awaited

Finding: an unhandled rejection was present.

### Level 3: verify the contract violation that triggers the rejection
- parse '{}' -> {}
- list required fields
- compare input vs requirements

Finding: {} violates the contract, so the rejection is expected.

---

## 6) Fix (before vs after)

### Before (contract violation + no await)
```js
it('should export an async function', () => {
  const result = generateMarkdown('{}', {});
  expect(result).toBeInstanceOf(Promise);
});
``` 

### After (contract compliant + await the promise)
```js
it('should export an async function', async () => {
  const result = generateMarkdown(EMPTY_REGISTRY);
  expect(result).toBeInstanceOf(Promise);
  await expect(result).resolves.toBeDefined();
});
``` 

---

## 7) Verification
- Run failing test alone -> PASS
- Run full suite -> PASS
- Run full suite multiple times -> PASS

---

## 8) What RED added (the takeaway)
This case was not solved by guessing better.
It was solved by making hidden assumptions explicit:
- Is the test input contract-compliant?
- Is every async operation awaited?
- Is there shared mutable state?

RED is an equalizer: it replaces expert intuition with a repeatable verification process.
