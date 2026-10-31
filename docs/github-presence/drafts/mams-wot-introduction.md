# MAMS Web of Things

Connect agents to devices through their Thing Descriptions.

MAMS WoT lets ASTRA/MAMS agents read, write and observe properties, invoke actions and subscribe to events using W3C Web of Things Thing Descriptions. The library selects interaction details from the TD, with bindings for HTTP, CoAP and MQTT.

> This GitHub repository is a mirror. Development, issues and merge requests are hosted at [mams-ucd/mams-wot on GitLab](https://gitlab.com/mams-ucd/mams-wot). Please submit changes there; see [CONTRIBUTING.md](CONTRIBUTING.md).

## Choose a starting point

| Goal | Location |
|---|---|
| Use the WoT library | `libraries/mams-astra-wot` and the library usage section below |
| Run agents against simulated Things | `examples/wot-test-agents` |
| Explore the apartment demonstrator | [Apartment application](applications/apartment/README.md) |
| Explore discovery and the WoT assistant | [WoT assistant](applications/wot-assistant/README.md) |
| Find the preserved event demonstration | [TPAC 2026 snapshot](tpac-plugfest-2026/README.md) |

## Run the basic demonstration

With JDK 17, Maven and access to the dependency repositories configured by the POM:

```sh
mvn clean install
cd examples/wot-test-agents
mvn compile astra:run
```

The example starts simulated Things and agents that exercise HTTP, CoAP and MQTT interactions. It uses local ports 8085, 5683 and 1884; keep these available. This basic demonstration does not require an LLM API key.

The apartment application is a larger demonstration with separate launch instructions and optional LLM-backed behaviour. Start with the basic examples before exploring it.

See the sections below for dependency versions, protocol support and limitations. This is work in progress: source availability should not be taken as a claim of complete WoT conformance.
