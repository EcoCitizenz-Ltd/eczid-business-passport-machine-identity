# ECZ-ID Business Passport & Machine Identity

![ECZ-ID Business Passport and Machine Identity trust-spine visual](https://raw.githubusercontent.com/EcoCitizenz-Ltd/.github/main/assets/repository-visuals/eczid-business-passport-machine-identity.jpg)

## One organisation. Many machines. One resolvable identity spine.

Modern organisations increasingly act through AI agents, MCP servers, APIs, plugins, SDKs, devices, services and software workloads.

The useful question is no longer only:

> Who is this company?

It is also:

> Which organisation stands behind this machine, service or agent, and what current evidence can a relying party independently review?

This repository is a practical guide to the current ECZ-ID parent/child identity model.

## Start here

- [View live ECZ-ID proof](https://resolver.ecocitizenz.org/p/ECZ-GB-RBS1NW)
- [Choose a free machine Passport](https://developers.ecocitizenz.com/get-started/free-passport/?utm_source=github&utm_medium=repository&utm_campaign=business-passport&utm_content=free-passports)
- [Explore EcoCitizenz](https://www.ecocitizenz.com?utm_source=github&utm_medium=repository&utm_campaign=business-passport&utm_content=business)
- [Open the Developer Gateway](https://developers.ecocitizenz.com?utm_source=github&utm_medium=repository&utm_campaign=business-passport&utm_content=developers)
- [Start with TrustOps](https://trustops.ecocitizenz.com/start?utm_source=github&utm_medium=repository&utm_campaign=business-passport&utm_content=start)

The free machine-Passport journey creates a free Business Passport when the organisation does not already have one. The seven child Passport identities are also free. Paid products add assurance, authority, monitoring, evidence, capacity, tooling or professional services; payment does not change the meaning of identity or public Resolver evidence.

---

## The current parent/child model

A parent Business Passport provides the organisational identity anchor.

The current machine identity layer has **exactly seven free child Passport families**:

```text
Organisation / Business Passport
|
+-- Agent Passport               AGENT_PASSPORT
+-- MCP Passport                 MCP_PASSPORT
+-- Plugin Passport              PLUGIN_PASSPORT
+-- API Passport                 API_PASSPORT
+-- IoT Passport                 IOT_DEVICE
+-- SDK Passport                 SDK_PASSPORT
+-- Service & Workload Passport  SERVICE_WORKLOAD_PASSPORT
```

A current child identifier uses:

```text
{parent_ecz_id}::{CURRENT_TYPE_CODE}-XXXXXX
```

Models, datasets, products, robots, vehicles, software packages, infrastructure and sector-specific assets can still matter. They may be **subjects, evidence, bindings, dependencies, relationships or use cases** beneath the appropriate current Passport family. They are not additional child Passport families and must not be encoded using historical catalogue-era child type codes.

The parent/child relationship helps a relying party review:

- who operates the surface;
- which parent organisation stands behind it;
- what relationship is asserted;
- which evidence is published;
- whether evidence is still current;
- whether lifecycle state has changed.

A parent identity or stronger Parent assurance does **not** automatically make every child safe, approved, compliant, VERIFIED or ASSURED. Parent strength belongs to the accountable organisation unless a child has its own legitimately established current state.

---

## Why a parent identity matters

Without a stable organisational anchor, machine identity is often reconstructed indirectly from domains, package publishers, repository ownership, certificates, cloud tenancy, email addresses or transient transport state.

Those signals can be useful, but they are not the same as a stable, resolvable operator identity.

A Business Passport provides an explicit identity reference around which machine relationships and evidence can be reviewed.

---

## Parent identity review checklist

Before relying on an organisation-operated machine surface, ask:

- [ ] Which organisation claims responsibility?
- [ ] What is its stable identity reference?
- [ ] Can that identity be independently resolved?
- [ ] Is the published evidence current enough for our policy?
- [ ] Which of the seven current machine Passport families fits the surface?
- [ ] What specific machine/service subject is linked to the child identity?
- [ ] What authority relationship is asserted?
- [ ] Has the child identity been changed, superseded, suspended, revoked or withdrawn?
- [ ] Where should lifecycle or incident changes be checked?
- [ ] Can the review be repeated later?
- [ ] What does our own relying-party policy require?

---

## Parent and child answer different questions

**Parent**

> Who is the organisation behind this surface?

**Child**

> Which particular machine identity is acting, and what family/relationship describes it?

Keeping those questions separate improves accountability without pretending identity is itself a security verdict.

---

## Example review flow

```text
Receive machine identity
        |
        v
Resolve child reference
        |
        v
Identify parent organisation
        |
        v
Review current published evidence
        |
        v
Check freshness / lifecycle
        |
        v
Apply local relying-party policy
        |
        v
Decide
```

---

## Canonical Resolver pattern

Human Resolver record:

```text
https://resolver.ecocitizenz.org/p/{URL-encoded ecz_id}
```

Machine proof document:

```text
https://api.ecocitizenz.com/api/p/{URL-encoded ecz_id}.json
```

A missing public record is absence of public ECZ-ID proof, not automatically a danger or trust verdict. An unreadable Resolver is unreadable; it must not be silently converted into absence.

---

## Developer integration

A typical resolver-first pattern is:

```text
machine / agent / API
        |
        v
ECZ-ID reference
        |
        v
Resolver
        |
        v
current published evidence
        |
        v
local policy
```

[Explore developer resources](https://developers.ecocitizenz.com?utm_source=github&utm_medium=repository&utm_campaign=business-passport&utm_content=integration)

---

## Explore child identities

The companion repository contains current, explicitly non-issued example fixtures for all seven machine Passport families and explains how wider domain concepts map into those families without creating extra Passport types.

[ECZ-ID Child Passport Examples](https://github.com/EcoCitizenz-Ltd/eczid-child-passport-examples)

---

## Public operator proof

**ECZ-ID public identity evidence - ECZ-GB-RBS1NW**
[View current public identity and evidence](https://resolver.ecocitizenz.org/p/ECZ-GB-RBS1NW)

Resolver evidence is published for review. It does not replace the relying party's security, legal, procurement or authorization decision.

---

## Automate parent-proof re-checks

A stable parent identity becomes more useful when relying systems can re-check its public evidence repeatedly.

For a known ECZ-ID parent reference, the ECZ-ID MCP Verifier can be used from GitHub Actions:

```yaml
- name: Re-check parent ECZ-ID posture
  uses: Ecocitizenz/ecz-id-mcp-verifier@v0.9.1
  with:
    target: ECZ-GB-RBS1NW
    policy: PREFER
```

[ECZ-ID MCP Verifier](https://github.com/Ecocitizenz/ecz-id-mcp-verifier)

This checks public Resolver posture for the supplied parent ECZ-ID. It does not infer the safety, assurance or approval of every child machine beneath that parent.
