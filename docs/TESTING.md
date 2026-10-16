# Testing Strategy

Use checks appropriate to project risk; no single check proves correctness or security.

Suggested tools:
- PHPCS with WordPress Coding Standards
- PHPUnit unit/integration tests
- PHPStan or another suitable static analyzer configured for WordPress
- JavaScript linting, type checking and tests when JS is present
- Staging/manual testing for actual workflows, permissions, upgrades and integrations

Consider tests for fresh activation, deactivation/reactivation, schema upgrades, missing dependencies, unauthorized users, invalid inputs, API timeouts/rate limits, multisite if supported, theme switching, accessibility and uninstall/data retention.

Report exact commands, actual results, checks not run and why, and remaining manual verification. Never claim an unrun test passed.
