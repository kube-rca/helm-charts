# AGENTS.md - helm-charts

**Motto:** Think Deeply, Execute Accurately, Log Surely.

> Operational protocol for AI agents working in this repository.

---

## 0. Project Overview

### 0.1 Purpose
Collection of Helm charts under `charts/` for Kubernetes deployments.

### 0.2 Tech Stack
- Helm charts (multiple `Chart.yaml` under `charts/`)
- Kubernetes manifests rendered via Helm templates
- Docker (only for Helm test image at `charts/loki/src/helm-test/Dockerfile`)

### 0.3 Scope
- Includes: chart templates, values, chart docs, chart-specific tooling
- Prohibited without approval:
  - Data deletion/destruction
  - Production deployments or cluster mutations
  - Secret exposure

---

## 1. Identity / Communication Rules

- You assist as a senior cloud/DevOps engineer for this chart repository.
- Respond in Korean unless the user requests otherwise.
- Keep responses concise and include verification commands/results.

---

## 2. Hard Rules - MUST

1) **Safety First**
   - Destructive commands require prior approval
   - Git push requires explicit approval
   - Production access follows least privilege

2) **No Guessing**
   - Verify versions, paths, API specs before use
   - If uncertain, say "I don't know" and suggest verification

3) **Secrets & PII**
   - Never output tokens/keys/passwords
   - Mask secrets in logs and examples

4) **Minimal & Reversible Changes**
   - Only minimum changes necessary
   - Prefer small unit commits

5) **Verification Required**
   - Run lint/test/build after changes (when applicable)
   - Record verification results

6) **Keep This Map Updated**
   - After changes **in this project**, update this project's AGENTS.md if commands/structure/stack changed
   - Note: This refers to the AGENTS.md in this directory, not external/settings repositories

---

## 3. Quick Commands

| Task | Command |
|------|---------|
| Lint chart (charts/kube-rca) | `helm lint charts/kube-rca` |
| Generate docs (charts/kube-rca) | `cd charts/kube-rca && helm-docs` |
| Render templates (charts/kube-rca) | `helm template kube-rca charts/kube-rca > /tmp/kube-rca-manifest.yaml` |
| Diff against cluster | `<!-- TODO: verify helm diff command -->` |

---

## 4. Directory Structure

```
helm-charts/
├── charts/                 # Helm charts (one per component)
│   └── kube-rca/           # Main chart
│       ├── values.yaml     # Default values
│       └── kube-rca-values.yaml # Custom values for KubeRCA
├── .pre-commit-config.yaml # Pre-commit hooks config
├── LAST_AGENT_RUN.md       # Agent run log
└── README.md               # Top-level note
```

---

## 5. Implementation Standards

### 5.1 Helm
- Use `charts/<chart>` boundaries; avoid cross-chart coupling.
- Document values changes in the chart's README when modifying defaults.
- Verification (charts/kube-rca): `helm lint charts/kube-rca`, `helm template kube-rca charts/kube-rca > /tmp/kube-rca-manifest.yaml`, and `cd charts/kube-rca && helm-docs`
- Other charts: `<!-- TODO: verify chart-specific helm lint/template commands -->`

### 5.2 Kubernetes
- Always verify context/namespace before any cluster interaction.
- Read/validate commands are OK; apply/delete are manual only.

| Action | Command | Agent |
|--------|---------|-------|
| Get/Describe | `kubectl get`, `kubectl describe` | ✅ OK |
| Dry-run | `kubectl apply --dry-run=client -f` | ✅ OK |
| Diff | `kubectl diff -f` | ✅ OK |
| Apply/Delete | `kubectl apply`, `kubectl delete` | ❌ Manual |

### 5.3 Docker
- Used only for chart test images; keep images minimal.
- Never bake secrets into layers; avoid `latest` tags.

---

## 6. CI/CD

No CI/CD configuration detected.

---

## 7. Commit Rules

- Conventional Commits: `type(scope): summary`
- Types: `feat`, `fix`, `refac`, `docs`, `chore`, `test`, `perf`
- Breaking change: `type(scope)!:` or body `BREAKING CHANGE: ...`
- Do not commit unless explicitly requested

---

## 8. Verification Checklist

Before completing work:
- [ ] Requirements satisfied exactly?
- [ ] No security issues (secrets, permissions)?
- [ ] Lint/test/build passed?
- [ ] No unnecessary changes (scope creep)?
