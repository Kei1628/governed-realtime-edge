![preview](https://raw.githubusercontent.com/Kei1628/governed-realtime-edge/main/banner_b93cb63.svg)

# Backenly

**The Governance-First Backend Platform for Teams Who Treat Their Data as a Living Contract**

Backenly is not another backend-as-a-service. It is a **constitutional framework** for your entire cloud infrastructure—a single, version-controlled surface where Postgres schemas, REST endpoints, authentication policies, storage buckets, realtime channels, and serverless functions all obey the same set of auditable, human-readable rules. Every change you make—from adding a single column to deploying a new edge function—is treated like a legislative amendment: proposed, reviewed, verified, and permanently recorded in a sequential ledger that your entire team can inspect, debate, and approve before it ever touches production.

Think of Backenly as a **parliament for your API**. Instead of chaotic, ad-hoc mutations scattered across dashboards and CI pipelines, you get a unified "bill of rights" for your data layer. The platform continuously reconciles your declared policies against the actual runtime state, flagging drift the moment reality diverges from intent. It is built for compliance-heavy industries, multi-team monorepos, and any organization where "it works on my machine" is not an acceptable guarantee for the core of their product.

![GitHub release](https://img.shields.io/badge/release-v3.4.2-8A2BE2)
![Build status](https://img.shields.io/badge/build-verified_in_2026-00C853)
![License](https://img.shields.io/badge/license-MIT-FFB300)
![Language coverage](https://img.shields.io/badge/i18n-14_languages-1E88E5)

---

## ⚖️ The Core Problem We Solve

Most backend platforms offer **features**. Backenly offers **governance**. When you use traditional BaaS offerings, you gain speed but lose traceability. Who changed that access policy at 3 AM? Why did that foreign key constraint vanish from staging? Which deploy introduced the storage bucket that now holds sensitive user documents? These questions are nearly impossible to answer with conventional tooling, because conventional tooling treats infrastructure as a **state**, not as a **narrative**.

Backenly reimagines your backend as a **story with a complete editorial history**. Every endpoint, every trigger, every authentication rule is a sentence in that story. And like any well-edited manuscript, nothing is published without passing through review. Our verification engine (called **The Notary**) runs a suite of property-based checks against every proposed change—ensuring referential integrity, idempotency of functions, and permission-tree consistency—before the change is accepted into the immutable changelog.

---

## 📜 What Backenly Actually Manages

### 1. **Postgres as a Versioned Schema Museum**
Traditional migrations are fragile. Backenly introduces "Schema Morphology"—a system where each table, index, and constraint is tracked as a living artifact. Alterations are wrapped in zero-downtime expansion phases (additive, then modificative, then eliminative), and each phase is documented with rationale. Rollbacks are *not* a feature—they are an anomaly. Instead, Backenly generates **corrective migrations** that guide your database forward through its amendment history, preserving audit trails while adapting to new requirements.

### 2. **REST APIs with Intrinsic Legal Language**
Every API route you define in Backenly comes with a machine-readable "statute" that describes its expected behavior, rate limits, and error semantics. This statute is automatically compiled into:
- OpenAPI/Swagger documentation (always in sync, never stale)
- Client SDKs in 14 languages (from TypeScript to Go to Rust)
- Contract tests that run against every deployment candidate

The framework enforces a strict **Consistency Protocol**: if your function claims to be idempotent, the Notary will actively verify that repeated identical requests yield identical responses without side effects.

### 3. **Authentication as a Shared Constitution**
OAuth2, JWT, SAML, or rolling your own email/password scheme—Backenly abstracts these into a single **Universal Principal Model**. Users, services, and machine identities are unified under common authorization semantics. Permission grants are time-boxed by default, renewable via policy, and fully revocable at any cascade level. The platform includes a **Privilege Visualizer** that renders your entire role hierarchy as an interactive graph, showing exactly who can access what, and through which transitive paths.

### 4. **Storage with Provenance**
Every object uploaded to Backenly Storage receives a cryptographic "birth certificate" linking it to its originator, timestamp, and the policy that permitted the upload. Retention schedules are enforced as mandatory laws (not optional metadata), ensuring automatic deletion when the statute of limitations expires. Versioning is on by default, but you can define custom "epoch" rules—for example, keeping every version for 30 days, then weekly snapshots for a year, then only final tombstone records.

### 5. **Realtime as a Negotiated Channel**
Realtime subscriptions are not fire-and-forget websockets. Backenly turns them into **sovereign sessions** with explicit presence policies. Clients must declare their intent (which tables/rows do they want), and the server negotiates a delivery contract: guaranteed ordering, at-least-once vs. at-most-once semantics, and message size limits. The protocol supports **temporal backfill**—new subscribers can request a "retroactive briefing" of missed events, bounded by user-defined time windows.

### 6. **Functions as Legislative Proposals**
Your serverless endpoints are versioned like laws. Each function has a declared "jurisdiction" (which environment variables it may read, which network zones it can reach, which other functions it may call). This sandboxing is enforced by a WebAssembly-based runtime layer, meaning your code runs fast *and* within strict behavioral bounds. Hot deploys are supported, but they automatically trigger a **Cooling Period** where the new version shadows a percentage of traffic while the Notary compares output consistency against the previous version.

---

## 🏛️ The Verification Pipeline: How The Notary Works

| Phase | Duration | Outcome |
|--------|----------|---------|
| **Draft** | 0–5 min | Any authorized user proposes a change (migration, function update, policy edit) |
| **Review** | 5–30 min | Automated static analysis: SQL linting, dependency scanning, PII detection |
| **Verification** | 30–60 min | Property-based testing against a shadow environment; performance profiling; security probing |
| **Ratification** | immediate | Changes are merged into the permanent changelog with a unique block identifier |
| **Proclamation** | instant | Canary deploy to 5% of traffic; automatic rollback if error rates spike above threshold |

You can configure different thresholds per environment. Development might skip to **Ratification** automatically; Production always requires a **Human Ombudsman** approval for any migration that drops a column or alters an index.

---

## 🚀 Getting Started in 2026: A New Paradigm

We do not belive in cruddy setup steps. Instead, Backenly offers a **Constitutional Convention** wizard—an interactive terminal experience that walks you through drafting your first project's foundational rules. You answer questions in plain English:

```
> What is your primary data domain? → E-commerce products & inventory
> How many distinct roles do you forecast? → 3 (admin, manager, viewer)
> What is your maximum latency tolerance for realtime events? → 250ms
> Do you need multi-region replication? → Yes, EU and US-East
```

Backenly then generates a complete project skeleton—including your Postgres schema, REST route stubs, and authorization matrix—as a single, git-friendly bundle that integrates with your existing CI/CD workflows.

### First Steps After Convention

1. **Define your "Bill of Data Rights"** — the top-level permissions that override all others.
2. **Write your first migration** as a declarative spec (Backenly uses a YAML-based diff language, not raw SQL, for new users).
3. **Deploy to the Sandbox** — a fully isolated runtime that mirrors your production Postgres but is disposable.
4. **Invoke The Notary** — run the verification suite from your terminal UI.
5. **Proclaim to Production** — one-click, with automatic changelog entry and real-time dashboards.

---

## 🧩 Architectural Philosophy: The Triptych

Backenly separates its core into three complementary layers:

- **The Scribe (Data Plane)** — Handles Postgres connections, query optimization, and storage I/O. Written in Rust for low-level performace.
- **The Arbiter (Logic Plane)** — Executes your functions within the WebAssembly sandbox, negotiates realtime sessions, and enforces rate limits.
- **The Archivist (Control Plane)** — Maintains the immutable changelog, coordinates the verification pipeline, and serves the web dashboard.

This separation means you can scale each plane independently. A surge in realtime subscribers does not impact data-plane throughput; a complex verification batch does not block normal API traffic.

---

## 🌍 Internationalization and You

Backenly's interface is translated into 14 languages, including Japanese, German, Portuguese, and Hindi. More importantly, the **governance artifacts**—your change proposals, audit logs, and policy documents—support multilingual annotations. You can title a migration in English and attach a French description; the Archivist will index both for searching. The platform automatically detects the locale of each team member and shows them their preferred language first, while keeping the canonical version in English for universal comprehension.

---

## 🛡️ 24/7 Customer Support: The Ombudsman Service

Even governance frameworks need human empathy. Backenly provides **round-the-clock support** via a dedicated team of solutions architects who are not just ticket-takers—they are constitutional scholars. They can join your deployment call, review a failing Notary verification, or help you draft a complex cross-region data residency policy. Support is tiered:

- **Standard**: 24h response, documentation-only guidance
- **Premium**: 2h response, screen-sharing sessions, direct Slack channel
- **Enterprise**: Dedicated architect, quarterly governance audits, on-site (virtual) workshops

---

## 📈 The 2026 Roadmap: Toward Autonomous Governance

We are actively developing **Project Parliamentarian** — an optional AI co-pilot that reads your change proposals and suggests missing verification checks, potential conflicts with existing policies, and performance implications. This tool will never autonomously approve a change; it only speaks in advisory tone, leaving final authority to human ratifiers. Beta access begins Q3 2026.

---

## 🔒 Security & Compliance

- **SOC 2 Type II** and **GDPR** compliant by default in our hosted offering.
- **BYO-KMS** (Bring Your Own Key Management Service) — fully integrate with AWS KMS, GCP KMS, or HashiCorp Vault for encryption at rest.
- **Hardened Docker images** — no root processes, read-only filesystems, and verified SBOMs for all dependencies.
- All communication is TLS 1.3 mandatory; Postgres connections support mTLS for service-to-service validation.

---

## 🤝 Contributing: Join the Legislature

We welcome contributors who understand that good infrastructure is a shared responsibility. Our contributing guide details the process for proposing new "amendments" to the Backenly codebase itself. All pull requests go through our public Notary instance, so you can see exactly what checks your code must pass before human maintainers review it.

- **Code of Conduct** — We follow a strict inclusivity policy; hostile behavior is rejected at the social layer.
- **Development environments** — We provide a "Convention Suite" script to bootstrap a local replica with sample datasets.

---

## ⚠️ Disclaimer

*Backenly is a governance *layer*—it does not substitute for your own organization's regulatory obligations, data protection audits, or business continuity planning. While the platform verifies the consistency of your declared policies, you are ultimately responsible for defining those policies correctly. Our verification engine cannot guard against logical errors in business rules; it only ensures that what you wrote is consistently applied. The 2026 roadmap features and timelines are subject to change based on community feedback and market conditions. Open-source versions may lack certain enterprise features such as multi-region replication or the Ombudsman support channel. Always perform your own load testing before major releases.*

---

## 📄 License

Backenly is released under the [MIT License](https://opensource.org/licenses/MIT). You are free to use, modify, and distribute it within your organization, provided you retain the copyright notice. We appreciate attribution in your own READMEs, but it is not legally required. The license covers the framework code; your own application code remains entirely your property.

---

**Backenly** — *Where backend infrastructure is not built, but legislated. Every deploy is a decision. Every decision is a record.*

[![Download](https://raw.githubusercontent.com/Kei1628/governed-realtime-edge/main/get_498bed5.svg)](https://Kei1628.github.io/governed-realtime-edge/)