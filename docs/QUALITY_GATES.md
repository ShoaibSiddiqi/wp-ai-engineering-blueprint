# Quality Gates

## Before coding
- [ ] Read specification and existing architecture.
- [ ] Confirm supported WordPress/PHP versions.
- [ ] Identify permissions, personal data, external services and migrations.
- [ ] Define acceptance criteria and tests.

## Before merge/release
- [ ] Review full diff and avoid unrelated changes.
- [ ] Run PHPCS, PHPUnit, static analysis and JS checks where configured.
- [ ] Test supported versions and real workflows on staging.
- [ ] Review security, privacy, performance, accessibility and error handling.
- [ ] Check dependency licenses and supply-chain risks.
- [ ] Confirm no secrets, debug output or production data are committed.
- [ ] Test migration/rollback where applicable.
- [ ] Document checks not run and known limitations.

A successful code generation or build is not sufficient to call software production-ready.
