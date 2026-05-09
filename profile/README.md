# vln-devsecops

Shared home for **DevSecOps automation, infrastructure modules, and
delivery building blocks** used across `VlinderSoftware`, `vln-*`,
`cpp4theselftaught`, and in-scope personal projects.

## What belongs here

- reusable GitHub Actions
- reusable Terraform modules and infrastructure patterns
- shared runner and utility repositories
- shared editorial/build automation that should not live in content repos
- org-wide operations docs, standards, and migration tracking

Application code, project-specific infrastructure, content repositories, and
deployment state stay with their owning repositories. This org is for the
**shared parts**.

## Current repository layout

| Repository | Purpose |
| --- | --- |
| `operations` | coordination workspace |
| `guidance` | standards, migration notes, and shared process/docs |
| `terraform-modules` | shared Terraform modules and infrastructure patterns |
| `actions-msvc` | GitHub Action for MSVC developer command prompt setup |
| `actions-build-paper` | GitHub Action for notebook/paper build and publish automation |
| `actions-generate-licenses` | GitHub Action for template-based licenses page generation |
| `actions-validate-coverage` | GitHub Action for unit test code coverage validation |
| `actions-autoversion` | GitHub Action for repository versioning automation |
| `github-runners` | shared GitHub runner infrastructure |
| `utils-system-cleanup` | shared cleanup utilities |
| `automation-books` | shared book build and editorial automation |

## Operating conventions

### Naming

Use short kebab-case repository names, usually following a
`<type>-<purpose>` pattern such as:

- `actions-msvc`
- `terraform-modules`
- `github-runners`
- `utils-system-cleanup`

See the guidance repo for more complete guidance.

### Branching and release flow

1. Repositories start on `dev` while still experimental.
2. Move to `main` once they are mature enough for pre-production use.
3. When first promoting to `main`, tag the current commit with both `v0.x` and
   `v0.x.y`.
4. Use moving `latest`, `vX` and `vX.Y` tags, and keep `vX.Y.Z` immutable.
5. When generally available, create a release branch such as `release/v1` and
   tag `v1`, `v1.0`, and `v1.0.0` from a README-accurate commit.

### Workflow naming

Prefix workflow filenames with an explicit category and a verb-led description:

- `ci_validate_terraform.yml`
- `ct_run_e2e.yml`
- `cd_deploy_infrastructure.yml`
- `_build_node.yml` for same-repo reusable workflows

### Dependency updates

1. Configure Dependabot for every ecosystem a repository actually uses.
2. Auto-approve or auto-merge **minor and patch** updates only when the test
   baseline is trustworthy.
3. Keep **major** updates manual unless explicitly decided otherwise.
4. If a repo does not yet have enough automated coverage, add Dependabot first
   and keep the approval flow gated.

## Notes for consumers

- prefer explicit `uses:` and module source references that point at the
  `vln-devsecops` repos directly; do not rely on old repository redirects
- prefer version tags over floating branch references in examples and docs
- expect some repositories to remain on `dev` until their interfaces settle
