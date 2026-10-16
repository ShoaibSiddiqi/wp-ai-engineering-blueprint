# Security Baseline

This checklist is not a complete security audit. Evaluate each feature's threat model and data sensitivity.

- Validate expected types, formats, ranges and allowlists.
- Sanitize data on input where appropriate; escape at output using context-specific functions such as `esc_html()`, `esc_attr()`, `esc_url()` or `wp_kses()`.
- Use `current_user_can()` or an equivalent capability check for privileged actions.
- Verify nonces for applicable state-changing requests. Nonces are not authentication or authorization.
- Give REST routes an intentional `permission_callback`; public access must be a deliberate design decision.
- Use `$wpdb->prepare()` for dynamic SQL values. Allowlist identifiers that cannot be parameterized.
- Secure AJAX/admin-post/background actions independently; hiding a UI control is not security.
- Keep secrets out of source control, logs, HTML and browser-side JavaScript.
- Use the WordPress HTTP API where appropriate; set timeouts, validate responses and assess SSRF risks for user-controlled URLs.
- Restrict uploads, filesystem access, redirects and archive extraction to necessary safe cases.
- Treat AI-generated output as untrusted; validate structured results, escape rendered content and restrict tool permissions.
- Minimize personal data collection; document storage, access, retention, export/erasure and uninstall behavior.
- Avoid exposing stack traces, SQL, credentials or sensitive internals to users.

Review questions: Can a low-privilege user trigger this? Can input affect SQL, HTML, JS, file paths or URLs? Are secrets exposed? Does the feature fail safely?
