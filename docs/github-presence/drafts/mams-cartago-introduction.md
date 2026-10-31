# Multi-Agent Microservices (MAMS)

Build web services whose behaviour is managed by agents.

MAMS is an architectural style for integrating multi-agent systems with microservice applications. This repository provides its ASTRA–CArtAgO reference implementation: agents expose HTTP resources, react to resource changes and interact with other services through web interfaces.

> This GitHub repository is a mirror. Development, issues and merge requests are hosted at [mams-ucd/mams-cartago on GitLab](https://gitlab.com/mams-ucd/mams-cartago). Please submit changes there; see [CONTRIBUTING.md](CONTRIBUTING.md).

## What can I build?

Use MAMS when a service needs to pursue goals or coordinate work as well as answer requests: for example, assigning deliveries, monitoring a process or managing connected devices.

Resources can be managed passively, with agents observing their changes, or actively, with agents participating in request decisions. Applications must implement the decision policy they need; extending an active agent alone does not establish a refusal policy.

Clients interact through HTTP without needing to understand ASTRA. Inside a service, multiple agents can cooperate using agent communication.

## Get started

Follow the [MAMS guide](https://guide.astralanguage.com/en/latest/mams/index.html), beginning with its first-service walkthrough. Use the dependency versions specified by the chosen example; tutorial versions and current framework versions may differ.

- [ASTRA language guide](https://guide.astralanguage.com/en/latest/)
- [MAMS example sources](https://gitlab.com/mams-ucd/mams-guide)
- [Web of Things integration](https://gitlab.com/mams-ucd/mams-wot)

MAMS uses Java 17 or later. Existing Maven publishing remains on its current infrastructure; mirroring this source does not relocate package repositories. See [LICENSE](LICENSE) for the source licence.
