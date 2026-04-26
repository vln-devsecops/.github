# vln-devsecops

Shared home for extracted **DevSecOps automation, infrastructure modules, and
delivery building blocks** used across `VlinderSoftware`, `vln-polaris`,
`cpp4theselftaught`, and related in-scope personal projects.

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
| `operations` | coordination workspace, standards, migration notes, and shared process/docs |
| `terraform-modules` | extracted shared Terraform modules and infrastructure patterns |
| `actions-msvc` | GitHub Action for MSVC developer command prompt setup |
| `actions-build-paper` | GitHub Action for notebook/paper build and publish automation |
| `actions-generate-licenses` | GitHub Action for license generation |
| `actions-validate-coverage` | GitHub Action for coverage validation |
| `actions-autoversion` | GitHub Action for repository version automation |
| `github-runners` | shared runner infrastructure |
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

### Branching and release flow

1. Repositories start on `dev` while still experimental.
2. Move to `main` once they are mature enough for pre-production use.
3. When first promoting to `main`, tag the current commit with both `v0.x` and
   `v0.x.y`.
4. Use moving `vX` and `vX.Y` tags, and keep `vX.Y.Z` immutable.
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

## Current migration/extraction direction

- reusable Terraform assets are being extracted from application repositories
  into `terraform-modules`
- shared book automation is being centralized in `automation-books`, with
  `workspace-books` as the first consumer
- project-owned repositories continue to keep application-specific logic and
  state, while shared parts move here only when the boundaries are clean

## Notes for consumers

- prefer explicit `uses:` and module source references that point at the
  `vln-devsecops` repos directly; do not rely on old repository redirects
- prefer version tags over floating branch references in examples and docs
- expect some repositories to remain on `dev` until their interfaces settle
