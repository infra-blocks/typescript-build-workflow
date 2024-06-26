# typescript-build-workflow
[![Release](https://github.com/infra-blocks/typescript-build-workflow/actions/workflows/release.yml/badge.svg)](https://github.com/infra-blocks/typescript-build-workflow/actions/workflows/release.yml)
[![Update From Template](https://github.com/infra-blocks/typescript-build-workflow/actions/workflows/update-from-template.yml/badge.svg)](https://github.com/infra-blocks/typescript-build-workflow/actions/workflows/update-from-template.yml)

Runs a set of conventional scripts to build Typescript projects.

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
    uses: infra-blocks/typescript-build-workflow/.github/workflows/workflow.yml@v1
    with:
      node-version-file: .nvmrc
    secrets:
      codecov-token: ${{ secrets.CODECOV_TOKEN }}
```

### Releasing

The releasing is handled at git level with semantic versioning tags. Those are automatically generated and managed
by the [git-tag-semver-from-label-workflow](https://github.com/infra-blocks/git-tag-semver-from-label-workflow).
