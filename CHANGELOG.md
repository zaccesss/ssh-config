# Changelog

All notable changes to this project are recorded here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Added

- Public key placeholders in each platform folder, with the `ssh-keygen` command for that platform
  and per-machine naming guidance (`<platform>/<key>.<device-name>.pub`)
- One-key-pair-per-machine guidance in the setup guide and a second machine in
  `allowed_signers.example`
- Initial release: SSH client config for macOS, Linux and Windows and an allowed signers example
- Setup and reference guides
- CI that parses each config on its real platform and fails on any private key

### Changed

- Tidied code comments and the contributor guide.
