# Vlinder Software's DevSecOps

Shared home for **DevSecOps automation, infrastructure modules, and
delivery building blocks** used across `VlinderSoftware`, `vln-*`,
`cpp4theselftaught`, and in-scope personal projects.

Public repositories in this org are made available free of charge,
"as is", with no warranty of any kind.

## What you'll find here

- reusable GitHub Actions
- reusable Terraform modules and infrastructure patterns
- shared runner and utility repositories
- shared editorial/build automation that should not live in content repos
- org-wide operations docs, standards, and migration tracking

Application code, project-specific infrastructure, content repositories, and
deployment state stay with their owning repositories. This org is for the
**shared parts**.

Some repositories are not publicly available: we share what we can.

### Current public repositories

| Repository | Purpose |
| --- | --- |
| `.github` | Contains only the README and whatever GitHub needs for this. |
| [`vln-devsecops/actions-msvc`](https://github.com/vln-devsecops/actions-msvc) | GitHub Action for MSVC developer command prompt setup.<br/>A fork of [ilammy/msvc-dev-cmd](https://github.com/ilammy/msvc-dev-cmd). |
| [`vln-devsecops/actions-generate-licenses`](https://github.com/vln-devsecops/actions-generate-licenses) | GitHub Action for generating comprehensive open source license reports from npm dependencies |
| [`vln-devsecops/actions-validate-coverage`](https://github.com/vln-devsecops/actions-validate-coverage) | A GitHub Action to validate unit test code coverage |
| [`vln-devsecops/actions-build-paper`](https://github.com/vln-devsecops/actions-build-paper) | GitHub action to build a ipynb into a PDF and a static GitHub page |
| [`vln-devsecops/terraform-modules`](https://github.com/vln-devsecops/terraform-modules) | Reusable Terraform modules, mostly for AWS infrastructure. |

## Notes for consumers

- prefer version tags over floating branch references in examples and docs
- expect some repositories to remain on `dev` and `v0.x` versions until their interfaces settle
