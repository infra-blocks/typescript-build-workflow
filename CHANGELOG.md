# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.1] - 2024-05-02

### Fixed

- Use `inputs.skip` at step level, and not at job level. Skipping at job level results in the same issue with
  required checks paths as skipping at the caller's workflow invocation site (with an `if` expression).

## [1.1.0] - 2024-04-19

### Added

- The skip intput to skip on the callee's side of a `worfklow_call`. Otherwise, when the workflow is skipped from
  the caller's side (with an `if` expression), the check path when the workflow was run is not the same as when
  it was skipped ( `outer / inner` vs. `outer` when skipped) !

## [1.0.0] - 2024-01-21

### Added

- First release!

[1.1.1]: https://github.com/infra-blocks/typescript-build-workflow/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/infra-blocks/typescript-build-workflow/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/infra-blocks/typescript-build-workflow/releases/tag/v1.0.0
