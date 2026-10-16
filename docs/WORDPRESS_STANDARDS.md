# WordPress Standards

Use current official documentation as the source of truth for API signatures, supported versions and directory policies. Do not rely solely on model memory.

- Follow WordPress Coding Standards for PHP, JavaScript, CSS and documentation where applicable.
- Use WordPress APIs instead of reimplementing core functionality.
- Internationalize user-facing strings when localization is expected.
- Use actions for side effects and filters to transform values; document custom hooks and accepted arguments.
- Use the Settings API when appropriate; sanitize stored settings and escape rendered values.
- Register REST routes on the proper lifecycle hook, validate parameters and use meaningful permission callbacks.
- Enqueue scripts/styles with WordPress functions and load them only where needed.
- Keep admin and frontend assets appropriately scoped.
- For themes, follow the template hierarchy, use semantic accessible markup and keep non-presentation functionality in plugins.
- Check official directory requirements if submitting to WordPress.org.

References:
- Plugins: https://developer.wordpress.org/plugins/
- Themes: https://developer.wordpress.org/themes/
- Coding standards: https://developer.wordpress.org/coding-standards/wordpress-coding-standards/
- REST API: https://developer.wordpress.org/rest-api/
- Plugin directory guidelines: https://developer.wordpress.org/plugins/wordpress-org/detailed-plugin-guidelines/
