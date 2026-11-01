# Engineering background

My engineering work spans enterprise networking and embedded telecom platforms.
I work across requirements, implementation, debugging, validation and technical
documentation, with particular interest in the boundary between hardware and software.

## Areas I bring to a team

| Area | Work context | Public example to inspect |
| --- | --- | --- |
| Systems and embedded software | C/C++, Embedded Linux/RTOS, HAL/SoC and bootloader integration | The public lab uses Python to make failure behavior easy to reproduce; a public C firmware implementation is not yet included |
| Networking and platform integration | Network platforms, hardware-specific behavior, trace-led root-cause analysis | [Reliability lab architecture](https://github.com/jyotirawattech/linux-network-reliability-lab/blob/main/docs/architecture.md) |
| Validation and release reasoning | Unit/system validation, design notes, collaboration across hardware and software teams | [Lab tests](https://github.com/jyotirawattech/linux-network-reliability-lab/tree/main/tests) and [release memo](https://github.com/jyotirawattech/linux-network-reliability-lab/blob/main/docs/leadership-memo.md) |
| Evidence and uncertainty | Stating the source, check time, assumptions and unresolved information | [Employer Posting Verifier](https://github.com/jyotirawattech/employer-posting-verifier) and its fictional fixtures |
| Workflow decisions | Making assumptions and prioritization rules inspectable | [Release Readiness Audit](https://github.com/jyotirawattech/release-readiness-audit) and its documented scoring contract |

## Professional context

- **Cisco — Software Engineer:** enterprise networking platform software, integration, debugging and validation.
- **NEC Technologies India — Junior Engineer:** embedded C and optical-access platform work, testing and design documentation.
- **Altran — Software Engineer:** bootloader, hardware-abstraction and SoC firmware integration during device bring-up.

This is a high-level account of my background. The public repositories are independent
examples of engineering methods, with their own source, tests and limitations.

## How I approach a technical problem

1. State the behavior and the evidence that would establish it.
2. Make a small failure case repeatable.
3. Record the measurement and the environment together.
4. Explain the decision, alternatives and remaining gaps.
5. Leave the next engineer a working command and an acceptance check.

In the reliability lab, that becomes a fault gateway, threshold-based monitor,
bounded timing objectives, automated tests, a design decision and a release memo.
That is the level of detail I want this portfolio to make easy to review.
