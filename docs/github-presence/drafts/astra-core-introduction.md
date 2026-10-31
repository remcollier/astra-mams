# ASTRA

Agent-oriented programming on the JVM.

ASTRA lets you express an agent's beliefs, goals and responses to events, while using Java libraries for the actions it performs. Its familiar syntax provides a practical starting point for exploring Belief–Desire–Intention (BDI) agents and multi-agent systems.

> This GitHub repository is a mirror. Development, issues and merge requests are hosted at [astra-language/astra-core on GitLab](https://gitlab.com/astra-language/astra-core). Please submit changes there; see [CONTRIBUTING.md](CONTRIBUTING.md).

## Start programming

Follow the [getting-started guide](https://guide.astralanguage.com/en/latest/getting-started.html) to create and run a Maven project. It lists the prerequisites and verified archetype version.

An agent responds to its startup goal like this:

```astra
agent Hello {
    module Console console;

    rule +!main(list args) {
        console.println("Hello from ASTRA");
    }
}
```

Save this class as `Hello.astra` in a configured ASTRA project. The project's launch configuration must select that agent; the getting-started archetype supplies its own `Main.astra` entry point.

## Explore

- [Programming guide and reference](https://guide.astralanguage.com/en/latest/)
- [Example projects](https://gitlab.com/astra-language/examples)
- [MAMS: agents as web services](https://guide.astralanguage.com/en/latest/mams/index.html)
- [Release notes](RELEASE_NOTES.md)

This repository contains the compiler, runtime, standard APIs and related integration modules. ASTRA packages are distributed through Maven Central. See [LICENSE](LICENSE) for the source licence.
