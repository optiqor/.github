<div align="center">

# Optiqor

**Production reliability and cost, for the teams running real workloads on Kubernetes.**

[![GitHub Discussions](https://img.shields.io/github/discussions/optiqor/kerno?label=discuss&color=222222&style=flat-square)](https://github.com/orgs/optiqor/discussions)
[![License](https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square)](https://github.com/optiqor/kerno/blob/main/LICENSE)
[![Go Report](https://goreportcard.com/badge/github.com/optiqor/kerno?style=flat-square)](https://goreportcard.com/report/github.com/optiqor/kerno)

</div>

---

## What we build

When something breaks in production, your APM dashboard is green and the kernel already knew minutes ago. When your cloud bill ships, half the cost lives in PRs nobody flagged. We build the tools that close those two gaps.

Two open-source products, one mission. Both ship as a single Go binary. Both run on bare metal, VMs, and Kubernetes. Both put the answer in your terminal, not a paid dashboard.

| Project | What it does | Status |
|---|---|---|
| **[kerno](https://github.com/optiqor/kerno)** | eBPF-based kernel incident diagnosis. `kerno doctor` collects six kernel signal dimensions, evaluates deterministic rules, optionally enriches with AI, and prints a ranked report of findings with copy-paste fixes. | Active. v0.2 in flight. |
| **[optiqor-cli](https://github.com/optiqor/optiqor-cli)** | Kubernetes cost analysis for every PR. Detects waste, proposes fixes, proves savings. Plugs into the CI pipeline so cost regressions never reach production. | Active. |

---

## Why

K8s observability is a crowded field. Most tools answer "is the dashboard green?" Optiqor answers two harder questions:

1. **What is the kernel about to do that the application layer hasn't noticed yet?** Datadog shows the dashboard. Kerno tells you the diagnosis.
2. **What does this change cost?** Most cost tools surface yesterday's spend. We move the gate left, into the PR review.

Both questions are answerable today. Both are unanswered for most teams. That's where we work.

---

## Get involved

| Audience | Start here |
|---|---|
| **Trying it** | [kerno install](https://github.com/optiqor/kerno#quickstart), [optiqor-cli](https://github.com/optiqor/optiqor-cli) |
| **Contributing code** | Each repo has its own `CONTRIBUTING.md`. We use Conventional Commits, DCO sign-off, and squash-merge. Good-first-issues are labeled across all repos. |
| **Reporting a bug** | The repo's issue templates walk you through it. Include kernel version, distro, and `kerno preflight` output for kerno bugs. |
| **Asking a question** | [GitHub Discussions](https://github.com/orgs/optiqor/discussions). Faster than a stale Slack channel. |
| **Security disclosure** | Private advisories via [GitHub Security Advisories](https://github.com/optiqor/kerno/security/advisories/new). Never a public issue. |

---

## How we work

- **Open source by default.** Both flagship products are Apache-2.0. The bits we keep private are operational, not the product.
- **Single-binary delivery.** No agent, no separate control plane, no cloud account required. `curl | sh` or `helm install` and you have it.
- **Linux-first, Kubernetes-first.** We test against multiple LTS kernels and the major managed K8s distros.
- **Boring technology.** Stdlib over framework. Polling when polling is enough. JSON over Protobuf without a reason.
- **Few false positives.** A rule that fires on a quiet system gets pulled. We'd rather miss a corner case than train operators to ignore alerts.

---

<div align="center">

**Optiqor** is built in the open by [Shivam Kumar](https://github.com/btwshivam) and a growing list of contributors.

If something you read here matches a problem you have, the door is open.

</div>
