<div align="center">

<img src="https://raw.githubusercontent.com/optiqor/optiqor-cli/main/docs/commands/optiqor-hori.jpg" alt="Optiqor" width="520">

# Detect. Fix. Prove.

### Kubernetes cost remediation that lives in the pull request.

**Optiqor catches cost waste in every Helm, Kustomize, and ArgoCD PR, ships the optimized commit in one click, and verifies the savings against the real cloud bill 30 days later.**

<br/>

[![Twitter](https://img.shields.io/badge/Follow-%40optiqor-1DA1F2?style=for-the-badge&logo=x&logoColor=white)](https://x.com/optiqor)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/company/optiqor)
[![Discussions](https://img.shields.io/badge/GitHub-Discussions-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/orgs/optiqor/discussions)
[![Email](https://img.shields.io/badge/team.optiqor%40gmail.com-4285F4?style=for-the-badge&logo=gmail&logoColor=white)](mailto:team.optiqor@gmail.com)

<br/>

[![License](https://img.shields.io/badge/CLI%20License-Apache--2.0-blue?style=flat-square)](https://github.com/optiqor/optiqor-cli/blob/main/LICENSE)
[![npm](https://img.shields.io/npm/v/@optiqor/cli?label=%40optiqor%2Fcli&style=flat-square)](https://www.npmjs.com/package/@optiqor/cli)
[![Stars](https://img.shields.io/github/stars/optiqor/kerno?style=flat-square)](https://github.com/optiqor/kerno)

</div>

---

## What Optiqor is

Kubernetes is where modern cloud waste hides. Teams over-provision pod requests by 3 to 5x. Clusters run at 20% utilization. Every Helm values change, Kustomize overlay, or ArgoCD Application PR is the moment the cost decision is made. Nobody is there.

Dashboards show you yesterday's spend. Autopilots take over your cluster as a black box. Cost calculators stopped at v0.1.1. The PR-time remediation layer is empty.

**Optiqor lives in the PR. Writes the diff. Verifies the savings. Catches the regression.**

Within 30 seconds of opening a Helm change, you get a comment with cost impact and a one-click **Apply Fix** button that pushes the optimized commit. We monitor every merged change for 7 days under the **Auto-Rollback Guarantee**. 30 days later we issue a cryptographically signed **Receipt** against the real cloud bill.

Obvious Kubernetes security misconfigurations get flagged in the same comment as a bonus. Cost is the wedge. Security is the side effect of parsing your chart anyway.

---

## The product surface

| Project | What it is | Status | License |
|---|---|---|---|
| [**optiqor-cli**](https://github.com/optiqor/optiqor-cli) | `npx @optiqor/cli analyze ./my-chart`. Zero-install Helm cost analyzer that runs offline in three seconds. The free, honest, directional answer. Bonus: flags obvious security misconfigurations on the way through. | Active | Apache-2.0 |
| **Optiqor Platform** | GitHub App + in-cluster agent + SaaS backend. Reads 30 days of Prometheus data, generates Apply Fix commits, issues signed savings Receipts, ships Auto-Rollback when reality drifts. Closed beta. | Beta | Proprietary (agent is Apache-2.0) |
| [**kerno**](https://github.com/optiqor/kerno) | eBPF kernel incident diagnosis. The kernel knew minutes before your APM did. Kerno tells you what. Sibling open-source project, separate product line. | Active | Apache-2.0 |

---

## How the cost platform works

```
1. PR opens          →  Optiqor parses the Helm / Kustomize / ArgoCD diff
2. Within 30s        →  PR comment with cost delta, Apply Fix button (security findings bundled in)
3. Click Apply Fix   →  We push a commit to your branch with the optimized values
4. Merge             →  We start a 7-day Auto-Rollback watch
5. Day 30            →  Signed Receipt: actual dollars saved, verified against the cloud bill
```

Three things are unique:

- **Apply Fix, not just commentary.** Every other tool tells you a number. We open the PR with the change.
- **Receipts, not promises.** We sign every claim against AWS Cost Explorer, Azure Cost Management, or a Hetzner capacity ledger. The savings are auditable.
- **Auto-Rollback, not "good luck."** If cost or reliability drifts beyond bounds in the 7 days after merge, we open the rollback PR ourselves.

---

## Kerno — system-level incident diagnosis

The other public product. Different problem space, same philosophy: live in the place where the decision is made, ship the answer in your terminal.

When something breaks in production, your APM dashboard is green and the kernel already knew minutes ago. Application logs say "connection refused" but the actual cause is DNS. Traces show 5-second latency but the bottleneck is cgroup CPU throttling. Engineers spend hours chasing the symptom because the cause lives below the application layer.

[kerno](https://github.com/optiqor/kerno) runs 30 seconds of eBPF signal collection across six dimensions (syscall latency, TCP flows, OOM events, disk I/O, scheduler delays, FD leaks), evaluates deterministic rules, and prints a ranked report of findings with copy-paste fixes. Optional AI enrichment adds plain-English root-cause analysis. Works on bare metal, VMs, EC2, GCE, and Kubernetes from a single Go binary.

```sh
curl -sfL https://raw.githubusercontent.com/optiqor/kerno/main/scripts/install.sh | sudo bash
sudo kerno doctor
```

| Highlights | |
|---|---|
| Six eBPF programs, CO-RE portable | Tested on kernel 5.15 through 6.17 |
| Zero false positives at idle | Rules that fire on a quiet host get pulled |
| Optional AI providers | Anthropic, OpenAI, Ollama (raw HTTP, no SDK lock-in) |
| Kubernetes-native | Helm chart, DaemonSet, Prometheus metrics, ServiceMonitor |
| Auto-graceful degradation | A failed eBPF program logs and skips, never bails the daemon |
| Single binary | Bare metal, VMs, EC2, GCE, Hetzner, K8s. One install path each. |

---

## Get started in 60 seconds

**Try the cost CLI** (no account, no cluster connection):

```sh
npx @optiqor/cli analyze ./my-helm-chart
```

A directional cost report in under three seconds, fully offline. Security findings come along for free.

**Diagnose a production incident with kerno**:

```sh
curl -sfL https://raw.githubusercontent.com/optiqor/kerno/main/scripts/install.sh | sudo bash
sudo kerno doctor
```

A 30-second eBPF capture, ranked findings, plain-English fixes.

**Want exact savings in your PRs?** The full Platform is in closed beta. Reach out at [team.optiqor@gmail.com](mailto:team.optiqor@gmail.com) to join the wait list.

---

## Year 1 scope (cost platform)

We own Kubernetes in 12 months instead of trying to own everything in 24.

**Clusters:** AWS EKS, Azure AKS, Hetzner Cloud K8s. GKE follows in Year 2.
**GitOps:** ArgoCD, Flux CD.
**VCS:** GitHub, GitLab. Bitbucket follows in Year 2.
**Templating:** Helm, Kustomize.

---

## How we work

- **OSS by default for what runs in your cluster.** Both public products and the in-cluster agent are Apache-2.0. The SaaS backend is proprietary. Regulated customers don't run closed-source binaries in production. We respect that.
- **Single-binary delivery.** No separate control plane, no Helm chart with 47 values. `curl`, `npx`, or `helm install` and you have it.
- **Few false positives.** A rule that fires on a quiet system gets pulled. Operator trust compounds, alert fatigue is permanent.
- **Boring technology.** Stdlib over framework. Postgres over the latest. Polling when polling is enough.
- **Build in the open.** Roadmaps, ADRs, and post-mortems live in GitHub Discussions.

---

## Contribute

Both public repos have full contributor guides:

- [optiqor-cli/CONTRIBUTING.md](https://github.com/optiqor/optiqor-cli/blob/main/CONTRIBUTING.md)
- [kerno/CONTRIBUTING.md](https://github.com/optiqor/kerno/blob/main/CONTRIBUTING.md)

Common ground:

- Conventional Commits. Squash merges. DCO sign-off (`git commit -s`).
- Good-first-issues are labeled in both repos.
- Slash commands in PRs: `/assign`, `/take`, `/lgtm`, `/merge`, `/hold`, `/retest`.
- Auto-release of stale claims after 10 days, contributor cap of 2 concurrent claims.

---

## Connect

<div align="center">

[<img src="https://img.shields.io/badge/X%20%2F%20Twitter-%40optiqor-1DA1F2?style=for-the-badge&logo=x&logoColor=white" alt="X / Twitter">](https://x.com/optiqor)
[<img src="https://img.shields.io/badge/LinkedIn-Optiqor-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">](https://www.linkedin.com/company/optiqor)
[<img src="https://img.shields.io/badge/Discussions-orgs%2Foptiqor-181717?style=for-the-badge&logo=github&logoColor=white" alt="Discussions">](https://github.com/orgs/optiqor/discussions)
[<img src="https://img.shields.io/badge/Email-team.optiqor%40gmail.com-4285F4?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">](mailto:team.optiqor@gmail.com)

</div>

---

<div align="center">

<sub>Built for platform engineers who got tired of being the cost department.</sub>

<sub>Security disclosure: <a href="https://github.com/optiqor/kerno/security/advisories/new">GitHub Security Advisories</a>. Never a public issue.</sub>

</div>
