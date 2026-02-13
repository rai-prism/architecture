# Prism Architecture

Welcome! This repository is where architectural decisions for
[Prism](https://gitlab.com/rai.onl/prism) are proposed, discussed, and
recorded.

## What is Prism?

Prism is an open source federated learning platform built in Rust. It provides
secure, scalable orchestration for distributed machine learning — coordinating
model training across edge devices and data silos, aggregating updates without
centralising sensitive data, and ensuring compliance with privacy regulations
and sovereignty requirements.

Data never leaves where it lives; only model improvements travel.

Prism sits within the broader Rai ecosystem: Prism trains models via federated
learning, [Shield](https://gitlab.com/rai.onl/shield) serves trained models
through a secure AI gateway, and [Arai](https://gitlab.com/rai.onl/arai)
orchestrates AI agents that consume those models. Agents on edge devices can
also participate as Prism clients, feeding training signals back from
operational environments.

## What this repository is for

This repository tracks architectural decisions using two complementary
approaches:

- **Decisions** capture internal technical and organisational choices — how
  Prism is built, structured, and maintained.

- **Comments** handle community-facing proposals — changes to public interfaces,
  features, behaviour, and integration patterns that affect how people use
  Prism.

These terms map to well-established practices — decisions are also known as
architecture decision records (ADRs), and comments are also known as requests
for comments (RFCs). We use plainer language to lower the barrier to
contribution.

Both approaches are open to everyone. You don't need to be a maintainer or a
regular contributor to submit a proposal. If you have an idea or see something
that could be improved, you're welcome here.

## How the process works

1. **Create an issue** using one of the issue templates (decision or comment) to
   signal your intent and invite early feedback.
2. **Draft a proposal** using the document templates in `templates/`.
3. **Submit a merge request** with your proposal in `decisions/` or `comments/`.
4. **Discuss** — for decisions, technical leads review over 7–14 days. For
   comments, the community discusses for a minimum of 14 days.
5. **Decision** — once consensus is reached, the proposal is merged and becomes
   part of the project's record.

The full process, including how consensus works, how disagreements are resolved,
and what happens with urgent decisions, is documented in the
[Omnifi Foundation handbook](https://handbook.omnifi.foundation/engineering/architecture/).

## Projects in scope

Proposals in this repository may affect any part of the Prism ecosystem:

**Coordination**
- Orchestration protocol and shared types
- Experiment lifecycle management (creation, rounds, completion)
- Client registry, selection strategies, and health tracking
- Model trail (immutable, append-only provenance record)
- Configuration loading and validation

**Aggregation**
- Federated averaging (FedAvg, FedProx, FedOpt, Scaffold)
- Byzantine-robust aggregation (Krum, trimmed mean, median)
- Hierarchical multi-tier aggregation
- Custom aggregation via Wasm plugins
- Secure aggregation via multi-party computation

**Privacy**
- Differential privacy (local and global)
- Trusted execution environment support (Intel TDX, AMD SEV-SNP, ARM CCA,
  AWS Nitro, NVIDIA H100 CC)
- Gradient compression and communication efficiency
- Data residency controls and geographic routing

**Client runtime**
- Core client logic (model updates, local training, gradient computation)
- Native client runtime with full OS access
- WASI client runtime for edge and constrained devices
- Battery-aware and network-aware scheduling

**Framework integration**
- Flower framework adapter
- NVIDIA FLARE adapter
- PyTorch, TensorFlow, scikit-learn, XGBoost, MONAI, Hugging Face

**Plugins**
- WASI plugin host (Wasmtime, sandboxing, lifecycle management)
- Plugin SDK for Rust with derive macros and WIT binding generation
- Cross-product compatibility with Shield and Arai

**Deployment**
- Standalone server binary (combined controller and aggregator)
- Container images and orchestration
- CLI tooling for experiment management and plugin development

**Transport**
- gRPC for standard deployments
- MQTT and CoAP for constrained IoT environments
- Adaptive transport selection

If your proposal spans multiple areas, note all affected projects in your
proposal so the right people can weigh in.

## Governance

Prism is governed by the [Omnifi Foundation](https://omnifi.foundation), a
community-driven organisation that stewards open source projects. The
architecture decision process — how proposals are written, reviewed, and
decided — is defined in the
[Omnifi Foundation handbook](https://handbook.omnifi.foundation/engineering/architecture/)
and applies equally to all contributors.

Decisions are made through consensus. Technical leads facilitate the process but
don't dictate outcomes. Every voice carries weight, and dissenting perspectives
are documented and valued. See the
[governance model](https://handbook.omnifi.foundation/engineering/architecture/governance/)
for full details.

## Getting started

New to the project? Here's how to get oriented:

1. **Browse existing proposals** in `decisions/` and `comments/` to see what's
   been decided and how proposals are structured.
2. **Check open merge requests** for proposals currently under discussion.
3. **Read the handbook** for
   [detailed process guidance](https://handbook.omnifi.foundation/engineering/architecture/).
4. **Open an issue** if you have questions — there are no bad questions.

## Repository structure

```
├── README.md              You are here
├── CONTRIBUTING.md        How to submit proposals
├── templates/
│   ├── decision.md        Decision template
│   └── comment.md         Comment template
├── decisions/             Accepted decisions
├── comments/              Accepted comments
└── .gitlab/
    └── issue_templates/
        ├── decision.md    Issue template for proposing a decision
        └── comment.md     Issue template for proposing a comment
```

## Code of conduct

All participation is subject to the
[Omnifi Foundation code of conduct](https://handbook.omnifi.foundation/CODE_OF_CONDUCT/).
We're committed to a welcoming, respectful, and inclusive environment.

## Licence

CC BY-SA 4.0 — see LICENCE for details.
