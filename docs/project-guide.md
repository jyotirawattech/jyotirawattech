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

## 2. Explain release coordination effort

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

## 3. Preserve uncertainty in a source check

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
