# Choose a project to inspect

Each entry starts with a question, a reproducible command and a concrete output.
Use a separate checkout for each project. All examples below use public or synthetic inputs.

## 1. Observe a service fail and return to health

**Repository:** [Linux Network Reliability Lab](https://github.com/jyotirawattech/linux-network-reliability-lab)

**Requires:** Python 3.11+ and Make on a machine that permits localhost sockets.

```sh
git clone https://github.com/jyotirawattech/linux-network-reliability-lab.git
cd linux-network-reliability-lab
make verify
```

**Finished output:** passing unit/integration tests, statement-line coverage and
a JSON result containing latency, rejected requests, outage detection and recovery detection.
Check that the result is PASS and all four experiment objectives are true.
The service stack runs for the experiment and shuts down afterward.

**Read next:** [architecture](https://github.com/jyotirawattech/linux-network-reliability-lab/blob/main/docs/architecture.md),
[decision record](https://github.com/jyotirawattech/linux-network-reliability-lab/blob/main/docs/adr/0001-portable-deterministic-faults.md),
[tests](https://github.com/jyotirawattech/linux-network-reliability-lab/tree/main/tests).

**Boundary:** the gateway injects application-layer behavior. A recovery measurement
records the monitor detecting restored health, not an autonomous repair of the service.
Host load changes the timings.

## 2. See when retries pay off

Clone [Retry Budget Lab](https://github.com/jyotirawattech/retry-budget-lab) and run this from its checkout with Python 3.11 or later:

```sh
python3 -m retry_budget_lab examples/recovery-window.json
```

The [worked result](https://github.com/jyotirawattech/retry-budget-lab/blob/565abee071e798aae501758c53ef7075346d6490/results/recovery-window.json) shows five synthetic requests. With no retries, one completes in five attempts. Fixed and exponential delays each complete three in thirteen attempts. Compare *which* requests finish as well as the totals. The clock and availability windows are simulated.

## 3. See which jobs finish after shutdown begins

Clone [Shutdown Boundary Lab](https://github.com/jyotirawattech/shutdown-boundary-lab) and run this from its checkout with Python 3.11 or later and access to localhost sockets:

```sh
python3 -m shutdown_lab
```

The [worked result](https://github.com/jyotirawattech/shutdown-boundary-lab/blob/c9f5a363af71ffa293872259b5c9f1df42872b1a/results/worked.json) shows three admitted jobs. All three are cancelled under immediate shutdown. With a fixed grace period, two finish and one is cancelled. The lab uses controlled job events on loopback, so the result illustrates the lifecycle policy under those conditions.

## 4. Check whether green CI refers to the artifact you released

Clone [Release Evidence Checker](https://github.com/jyotirawattech/release-evidence-checker) and run this from its checkout with Python 3.11 or later:

```sh
python3 -m release_evidence demo
```

The [worked result](https://github.com/jyotirawattech/release-evidence-checker/blob/09717ed9f75c495f25dc09fb3471e64d3e9d1064/results/worked.json) compares a green-status rule with checks on the supplied artifact, publication and CI records. Only one of the nine green-status claims passes the consistency checks in this synthetic set. The others show a mismatch, incomplete preparation, or an unconfirmed push. The CLI checks consistency of supplied records. It cannot authenticate the records or check a live deployment.

## 5. Explain release coordination effort

**Repository:** [Release Readiness Audit](https://github.com/jyotirawattech/release-readiness-audit)

**Requires:** Node.js 18+; no third-party packages.

```sh
git clone https://github.com/jyotirawattech/release-readiness-audit.git
cd release-readiness-audit
npm test
npm run audit:example
```

**Finished output:** the supplied qualified fictional example returns a 17/21
friction score, an estimate of 10 person-hours per month, and suggested next steps.
Inspect the scoring contract and the negative examples to understand what changes the result.

**Read next:** [audit contract](https://github.com/jyotirawattech/release-readiness-audit/blob/main/references/audit-contract.md).

**Boundary:** estimates come from aggregate answers. The tool does not scan CI,
detect configuration drift, certify compliance or approve a release. Its README
separately discloses an optional commercial route; the local example is free.

## 6. Preserve uncertainty in a source check

**Repository:** [Employer Posting Verifier](https://github.com/jyotirawattech/employer-posting-verifier)

**Requires:** Python 3.9+ for the standalone core; no installation for fixture mode.

```sh
git clone https://github.com/jyotirawattech/employer-posting-verifier.git
cd employer-posting-verifier
python3 -m employer_posting_verifier --fixture fixtures/fictional_batch.json
python3 -m unittest discover -s tests -v
```

**Finished output:** observations for five fictional Greenhouse cases. Inaccessible,
incomplete, conflicting or absent first-time evidence must remain Unknown.
Fixture mode makes no source requests.

**Read next:** [status semantics and source boundaries](https://github.com/jyotirawattech/employer-posting-verifier#status-semantics).

**Boundary:** Open means the post appeared in a complete published-board response.
It does not establish employer authenticity, candidate eligibility or an available
application route. This guide uses the fictional fixture; live operation has separate gates.
