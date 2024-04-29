# typescript-build-workflow
[![Git Tag Semver From Label](https://github.com/infrastructure-blocks/typescript-build-workflow/actions/workflows/git-tag-semver-from-label.yml/badge.svg)](https://github.com/infrastructure-blocks/typescript-build-workflow/actions/workflows/git-tag-semver-from-label.yml)
[![Update From Template](https://github.com/infrastructure-blocks/typescript-build-workflow/actions/workflows/update-from-template.yml/badge.svg)](https://github.com/infrastructure-blocks/typescript-build-workflow/actions/workflows/update-from-template.yml)

<<<<<<< HEAD
Runs a set of conventional scripts to build Typescript projects.
=======
This repository is a template for creating reusable GitHub Actions Workflows. Go through the below checklist
upon instantiating this template:
- Remove the [trigger update from template workflow](.github/workflows/trigger-update-from-template.yml)
- Edit the content of [the placeholder](.github/workflows/workflow.yml) for your reusable workflow.
- Update the status badges:
    - Remove the `Trigger Update From Template` status badge.
    - Add the `Update From Template` status badge.
    - Rename the rest of the links to point to the right repository.
- Edit this document and update the relevant sections
- Prepare the [changelog](CHANGELOG.md) for the first version of the module that will be released.
>>>>>>> template/master

## Inputs

|       Name        | Required | Description                                                                                                                                                                  |
|:-----------------:|:--------:|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| node-version-file |  false   | The NodeJs version file passed to actions/setup-node. One of `node-version-file` or `node-version` should be provided.                                                       |
|   node-version    |  false   | The NodeJs version passed to actions/setup-node. One of `node-version-file` or `node-version` should be provided.                                                            |
|       skip        |  false   | A boolean indicating whether to skip the workflow. This is to workaround the required checks discrepancy when the workflow is skipped from the caller. It defaults to false. |

## Secrets

|     Name      | Required | Description                                 |
|:-------------:|:--------:|---------------------------------------------|
| codecov-token |  false   | The Codecov token to publish code coverage. |

## Outputs

N/A

## Permissions

|  Scope   | Level | Reason                         |
|:--------:|:-----:|--------------------------------|
| contents | read  | Required to checkout the code. |

## Concurrency controls

N/A

## Timeouts

N/A

## Usage

```yaml
name: Build

on:
  push: ~

permissions:
  contents: read

jobs:
  build:
    uses: infrastructure-blocks/typescript-build-workflow/.github/workflows/workflow.yml@v1
    with:
      node-version-file: .nvmrc
    secrets:
      codecov-token: ${{ secrets.CODECOV_TOKEN }}
```

### Releasing

The releasing is handled at git level with semantic versioning tags. Those are automatically generated and managed
by the [git-tag-semver-from-label-workflow](https://github.com/infrastructure-blocks/git-tag-semver-from-label-workflow).
