# ECZ-ID Business Passport & Machine Identity

## One organisation. Many machines. One resolvable identity spine.

Modern organisations increasingly act through AI agents, MCP servers, APIs, software workloads, models, datasets, devices and automated services.

The useful question is no longer only:

> Who is this company?

It is also:

> Which organisation stands behind this machine, service or agent, and what current evidence can a relying party independently review?

This repository is a practical guide to the ECZ-ID parent/child identity model.

## Start here

- [View live ECZ-ID proof](https://resolver.ecocitizenz.org/passport/ECZ-GB-RBS1NW)
- [Explore EcoCitizenz](https://www.ecocitizenz.com?utm_source=github&utm_medium=repository&utm_campaign=business-passport&utm_content=business)
- [Open the Developer Gateway](https://developers.ecocitizenz.com?utm_source=github&utm_medium=repository&utm_campaign=business-passport&utm_content=developers)
- [Start with TrustOps](https://trustops.ecocitizenz.com/start?utm_source=github&utm_medium=repository&utm_campaign=business-passport&utm_content=start)

---

## The parent/child model

A parent Business Passport provides the organisational identity anchor.

Child identities can represent specific machine or operational surfaces beneath that organisation:

```text
Organisation
|
+-- API
+-- AI Agent
+-- MCP surface
+-- Software
+-- Dataset
+-- AI Model
+-- IoT Device
+-- Product
+-- Other machine or infrastructure identities
```

The relationship helps a relying party review:

- who operates the surface
- which parent organisation stands behind it
- what relationship is asserted
- which evidence is published
- whether evidence is still current
- whether lifecycle state has changed

A parent identity does not automatically make every child safe, approved or compliant.

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
- [ ] What specific machine or service is linked to the parent?
- [ ] What authority relationship is asserted?
- [ ] Has the child identity been changed, superseded or withdrawn?
- [ ] Where should lifecycle or incident changes be checked?
- [ ] Can the review be repeated later?
- [ ] What does our own relying-party policy require?

---

## Parent and child answer different questions

**Parent**

> Who is the organisation behind this surface?

**Child**

> Which particular API, agent, software workload, machine or product is acting?

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

The companion repository contains practical examples across APIs, agents, software, models, datasets, devices, products and other machine surfaces.

[ECZ-ID Child Passport Examples](https://github.com/EcoCitizenz-Ltd/eczid-child-passport-examples)

---

## Public operator proof

**ECZ-ID VERIFIED - ECZ-GB-RBS1NW**

[View current public identity and evidence](https://resolver.ecocitizenz.org/passport/ECZ-GB-RBS1NW)

Resolver evidence is published for review. It does not replace the relying party's security, legal, procurement or authorization decision.

---

## Automate parent-proof re-checks

A stable parent identity becomes more useful when relying systems can re-check its public evidence repeatedly.

For a known ECZ-ID parent reference, the ECZ-ID MCP Verifier can be used from GitHub Actions:

```yaml
- name: Re-check parent ECZ-ID posture
  uses: Ecocitizenz/ecz-id-mcp-verifier@v0.8.4
  with:
    target: ECZ-GB-RBS1NW
    policy: PREFER
```

[ECZ-ID MCP Verifier](https://github.com/Ecocitizenz/ecz-id-mcp-verifier)

This checks public Resolver posture for the supplied parent ECZ-ID. It does not infer the safety of every child machine beneath that parent.
