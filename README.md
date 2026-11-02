# Jyoti Rawat Tech

### Software Engineer · Embedded Linux · Networking · Reliability

I work on C/C++, embedded Linux, platform integration, debugging and validation.
My background spans enterprise networking and telecom systems. I’m interested in
how software behaves across hardware variants, how we detect failures, and what
evidence makes a release decision easier to defend.

Here I’m building small, reproducible projects that make those questions inspectable.

[LinkedIn](https://www.linkedin.com/in/jyotirawattech/) ·
[LeetCode](https://leetcode.com/u/user0592I/) ·
[Engineering writing](https://jyotirawattech.substack.com/) ·
[Engineering background](docs/engineering-background.md)

## Start with the reliability lab

**What happens between a service failing and a monitor noticing?**

The [Linux Network Reliability Lab](https://github.com/jyotirawattech/linux-network-reliability-lab)
runs a localhost HTTP service behind a programmable fault gateway. It injects
delay, rejects every third request in one scenario, and simulates a service outage.
A threshold-based monitor measures when it detects failure and the subsequent return to health.

- Python standard library; no package installation needed.
- Unit and integration tests, an 80% statement-line coverage gate, and Linux CI on Python 3.11 and 3.13.
- Architecture diagram, decision record, measured results and a leadership/release memo.
- The public verification record reports 9 passing tests and 81.4% statement-line coverage.

```sh
git clone https://github.com/jyotirawattech/linux-network-reliability-lab.git
cd linux-network-reliability-lab
make verify
```

[Read the architecture](https://github.com/jyotirawattech/linux-network-reliability-lab/blob/main/docs/architecture.md) ·
[Inspect the test results](https://github.com/jyotirawattech/linux-network-reliability-lab/blob/main/docs/results/verification-2026-09-02.md) ·
[View CI](https://github.com/jyotirawattech/linux-network-reliability-lab/actions)

The faults are application-layer delay and request rejection. Kernel packet loss,
TCP retransmission and production recovery remain separate questions.

## Selected projects

| Project | Question it helps answer | Inspect or reproduce |
| --- | --- | --- |
| [Linux Network Reliability Lab](https://github.com/jyotirawattech/linux-network-reliability-lab) · Python | Does the monitor detect sustained failure and recovery within its lab objectives? | Fault scenarios, state machine, tests, CI and measured evidence |
| [Release Readiness Audit](https://github.com/jyotirawattech/release-readiness-audit) · JavaScript | Where does a release workflow spend coordination effort? | Deterministic local calculator, eight aggregate inputs, documented scoring and fictional examples |
| [Employer Posting Verifier](https://github.com/jyotirawattech/employer-posting-verifier) · Python | What can a source check establish, and when must it return Unknown? | Greenhouse-specific prototype, fictional fixtures, source-linked observations and tests |
| [C-Tutorials: LeetCode solutions](https://github.com/jyotirawattech/C-Tutorials/blob/master/leetcode/README.md) · C | How do algorithm choices, pointer ownership and edge cases behave in C? | Accepted-source archive with submission provenance; local compilation and test results recorded separately |

The release audit calculates from supplied answers; it does not inspect a deployment.
The posting verifier records evidence; it does not authenticate employers or certify a job’s safety.

[Choose a project and run its example →](docs/project-guide.md)

## Engineering background

I’m a Software Engineer at Cisco, with earlier embedded software roles at NEC
Technologies India and Altran. My work has included platform integration,
trace-led debugging, unit/system validation, requirements and design documentation,
and working across hardware, ASIC, QA and infrastructure teams.

My foundation is C/C++, Embedded Linux/RTOS, HAL/SoC integration, networking,
GDB and platform validation. Python and JavaScript appear here in the public tools
where their implementation can be inspected. I also hold the Cisco Certified AI
Technical Practitioner credential.

I’m developing the connection between systems depth and technical leadership:
clear scope, testable acceptance criteria, explicit trade-offs and useful handovers.
The lab’s decision record and release memo are public examples of that approach.

## What’s next

The next planned lab experiment is a Linux network namespace with `tc netem`,
comparing kernel-level delay/loss against the portable gateway model. It is a
planned extension; the repository’s current evidence covers the portable experiment.

These are independent projects using public or synthetic inputs. Their results
describe the demonstrated test environment; they do not disclose employer code,
customer data or internal architecture.
