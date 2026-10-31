# ASTRA/MAMS GitHub presence — proposal

Draft for review, 31 October 2026. Nothing has been published or configured.

## Recommended shape

Create one GitHub organisation for the ASTRA/MAMS ecosystem (name to be chosen). Keep the existing GitLab groups as the development home initially. Each source repository gets its own one-way GitHub mirror; do not combine ASTRA and MAMS into a new monorepo.

```text
GitHub organisation
├── .github                 organisation profile; maintained on GitHub
├── astra-core              ← gitlab.com/astra-language/astra-core
├── mams-cartago             ← gitlab.com/mams-ucd/mams-cartago
├── mams-wot                 ← gitlab.com/mams-ucd/mams-wot
├── astra-docs               ← gitlab.com/astra-language/astra-docs
└── vscode-language-astra    ← gitlab.com/astra-language/vscode-language-astra
```

Start with the profile, astra-core and mams-cartago. Add mams-wot once its public packaging and licence are ready. Mirror the documentation and editor extension next. Pin the three main projects and the guide repository on the organisation page. Individual runnable example repositories can follow once their dependencies have been checked; the GitLab examples URL is a subgroup, not one repository to mirror.

The visitor's path should be: understand the relationship → choose language, service framework or WoT → run a small example → read the guide → contribute upstream.

## What to mirror

| Material | Initial policy |
|---|---|
| Source, tests, build files and documentation | Preserve the complete tracked tree of each selected repository. |
| Commit history | Preserve history and authorship, rather than uploading a source ZIP. Review historical contents before publication. |
| Branches and tags | Mirror public upstream branches and tags initially, after reviewing their scope. Verify the actual default branch per repository; do not assume `main`. |
| README and CONTRIBUTING | Commit improvements in GitLab so both hosts receive identical files. |
| Existing licences and attribution | Preserve exactly. ASTRA core and MAMS have local LICENSE files; verify each repository independently. No root licence was found in this mams-wot checkout. |
| Guide source | Mirror astra-docs; keep guide.astralanguage.com as the documentation URL and its existing publishing route. |
| Maven packages | Keep existing publishing and resolution endpoints. A Git mirror does not copy package registries. |
| Issues, merge requests, discussions and project boards | Keep on GitLab. Disable GitHub Issues, Discussions and Wiki initially. Pull requests can still arrive; explain the upstream route and close them courteously with a link. |
| Release pages, binaries and attachments | Not copied by Git mirroring. Tags are mirrored; link existing release notes and published artifacts. Add GitHub releases later only if maintained automatically. |
| CI variables, credentials and deployment configuration outside Git | Do not transfer. Keep build and release execution upstream. Review tracked automation before enabling any GitHub Actions. |
| Local outputs, `.env`, runtime history and private datasets | Do not add. A mirror includes anything already committed, including old revisions; .gitignore does not remove history. |
| Submodules and Git LFS, if present | Inventory separately: Git references alone do not establish that external repositories or LFS objects are available. |

Do not filter application directories out of mams-wot while describing it as an exact mirror. Its library, examples, apartment demonstrator and WoT assistant currently share a build. Keep that structure and improve navigation; splitting repositories is separate work.

## Public presentation

Use short repository descriptions:

- astra-core: “Agent-oriented programming on the JVM: beliefs, goals, plans and Java integration.”
- mams-cartago: “Multi-Agent Microservices: HTTP resources and agent-managed services with ASTRA and CArtAgO.”
- mams-wot: “Connect MAMS agents to Web of Things devices through Thing Descriptions.”

Suggested topics, applied only where relevant: `astra`, `multi-agent-systems`, `bdi`, `agent-oriented-programming`, `java`, `microservices`, `web-of-things`, `wot`, `iot`.

No empty badges, unverified release numbers or invented citation details. Keep the existing technical README material below a concise introductory section. The proposed README files are opening sections, not replacements for module documentation.

## Draft files and destinations

| Draft | Destination |
|---|---|
| [Organisation profile](drafts/organisation-profile.md) | `.github` repository → `profile/README.md` |
| [ASTRA README opening](drafts/astra-core-introduction.md) | astra-core → opening of `README.md` |
| [MAMS README opening](drafts/mams-cartago-introduction.md) | mams-cartago → opening of `README.md` |
| [WoT README opening](drafts/mams-wot-introduction.md) | mams-wot → opening of `README.md` |
| [Contribution policy](drafts/CONTRIBUTING.md) | Each mirrored repository → `CONTRIBUTING.md` |
| [Setup runbook](MIRRORING.md) | Maintainer reference; not visitor-facing copy |

The profile deliberately uses working GitLab and guide links until the GitHub organisation exists. Substitute GitHub links for the mirrored source entry points at launch, retaining explicit upstream links in repository notices.

## Evidence and unresolved details

The [public guide](https://guide.astralanguage.com/en/latest/) and [getting-started page](https://guide.astralanguage.com/en/latest/getting-started.html) informed the language description. Local astra-core, mams-cartago, astra-docs and mams-wot checkouts informed repository relationships and the MAMS description. The public MAMS chapter could not be fetched in this session, so its local documentation source was used.

Version wording needs reconciliation: the public guide homepage names ASTRA 2.8.4 / MAMS 2.5.9, while this mams-wot POM uses ASTRA 2.8.9 / MAMS 2.5.11. The getting-started guide pins archetype 2.8.2. These can represent different verification targets; do not call any one of them “latest” without checking published artifacts. Drafts link the guide instead of inventing a new version combination.

Before launch: choose organisation ownership/name; confirm project visibility and default branches; review licences and history; verify anonymous Maven dependency resolution; and run each advertised example from a clean checkout. Existing local builds are not evidence that a new visitor can resolve everything.
