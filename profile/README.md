<div align="center">

<img src="https://raw.githubusercontent.com/optiqor/optiqor-cli/main/docs/commands/optiqor-hori.jpg" alt="Optiqor" width="520">

### The GitOps-native cost and security layer for Kubernetes

**Every Helm PR, reviewed by an AI that ships the fix.**

<br/>

[![Website](https://img.shields.io/badge/optiqor.dev-1a1a1a?style=for-the-badge&logoColor=white)](https://optiqor.dev)
[![Twitter](https://img.shields.io/badge/Follow-%40optiqor-1DA1F2?style=for-the-badge&logo=x&logoColor=white)](https://x.com/optiqor)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/company/optiqor)
[![Discussions](https://img.shields.io/badge/GitHub-Discussions-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/orgs/optiqor/discussions)

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

Within 30 seconds of opening a Helm change, you get a comment with cost impact, security findings, and a one-click **Apply Fix** button that pushes the optimized commit. We monitor every merged change for 7 days under the **Auto-Rollback Guarantee**. 30 days later we issue a cryptographically signed **Receipt** against the real cloud bill.

---

## The product surface

| Project | What it is | Status | License |
|---|---|---|---|
| [**optiqor-cli**](https://github.com/optiqor/optiqor-cli) | `npx @optiqor/cli analyze ./my-chart`. Zero-install Helm cost analyzer that runs offline in three seconds. The free, honest, directional answer. Also flags obvious security misconfigurations on the way through. | Active | Apache-2.0 |
| [**Optiqor Platform**](https://optiqor.dev) | GitHub App + in-cluster agent + SaaS backend. Reads 30 days of Prometheus data, generates Apply Fix commits, issues signed savings Receipts, ships Auto-Rollback when reality drifts. Closed beta. | Beta | Proprietary (agent is Apache-2.0) |
| [**kerno**](https://github.com/optiqor/kerno) | eBPF kernel incident diagnosis. `kerno doctor` answers the question "the dashboard is green, but what is the kernel about to do?" Sibling project, separate product line. | Active | Apache-2.0 |

---

## How it actually works

```
1. PR opens          →  Optiqor parses the Helm / Kustomize / ArgoCD diff
2. Within 30s        →  PR comment with cost delta, security findings, Apply Fix button
3. Click Apply Fix   →  We push a commit to your branch with the optimized values
4. Merge             →  We start a 7-day Auto-Rollback watch
5. Day 30            →  Signed Receipt: actual dollars saved, verified against the cloud bill
```

Three things are unique:

- **Apply Fix, not just commentary.** Every other tool tells you a number. We open the PR with the change.
- **Receipts, not promises.** We sign every claim against AWS Cost Explorer, Azure Cost Management, or a Hetzner capacity ledger. The savings are auditable.
- **Auto-Rollback, not "good luck."** If cost or reliability drifts beyond bounds in the 7 days after merge, we open the rollback PR ourselves.

---

## Get started in 60 seconds

**Try the CLI for free** (no account, no cluster connection):

```sh
npx @optiqor/cli analyze ./my-helm-chart
```

That's it. A directional cost report and security findings in under three seconds, fully offline.

**Want exact savings?** [Install the Platform](https://optiqor.dev/get) into your cluster. The agent connects your real Prometheus data and your real cloud bill to every PR comment.

**Building Kubernetes observability?** Check out [kerno](https://github.com/optiqor/kerno) for the kernel-level side of the story.

---

## Year 1 scope

We own Kubernetes in 12 months instead of trying to own everything in 24.

**Clusters:** AWS EKS, Azure AKS, Hetzner Cloud K8s. GKE follows in Year 2.
**GitOps:** ArgoCD, Flux CD.
**VCS:** GitHub, GitLab. Bitbucket follows in Year 2.
**Templating:** Helm, Kustomize.

We do not currently support: Terraform-only stacks (use Infracost), pure VM/Lambda cost (use Vantage), or runtime security posture (use Wiz). When we work, we work well. When we don't, we say so and link you to who does.

---

## How we work

- **OSS by default for what runs in your cluster.** The CLI and the in-cluster agent are Apache-2.0. The SaaS backend is proprietary. Regulated customers don't run closed-source binaries in production. We respect that.
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

[<img src="https://img.shields.io/badge/Website-optiqor.dev-1a1a1a?style=for-the-badge" alt="Website">](https://optiqor.dev)
[<img src="https://img.shields.io/badge/X%20%2F%20Twitter-%40optiqor-1DA1F2?style=for-the-badge&logo=x&logoColor=white" alt="X / Twitter">](https://x.com/optiqor)
[<img src="https://img.shields.io/badge/LinkedIn-Optiqor-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">](https://www.linkedin.com/company/optiqor)
[<img src="https://img.shields.io/badge/YouTube-%40optiqor-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="YouTube">](https://www.youtube.com/@optiqor)
[<img src="https://img.shields.io/badge/Discussions-orgs%2Foptiqor-181717?style=for-the-badge&logo=github&logoColor=white" alt="Discussions">](https://github.com/orgs/optiqor/discussions)
[<img src="https://img.shields.io/badge/Email-team%40optiqor.dev-4285F4?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">](mailto:team@optiqor.dev)

</div>

---

<div align="center">

<sub>Built for platform engineers who got tired of being the cost department.</sub>

<sub>Security disclosure: <a href="https://github.com/optiqor/kerno/security/advisories/new">GitHub Security Advisories</a>. Never a public issue.</sub>

</div>
