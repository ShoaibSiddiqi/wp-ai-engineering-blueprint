# Architecture Guidelines

## Choose proportionally
Do not impose a framework on every plugin. A small plugin may need a few files; a larger plugin may benefit from modules and service classes. Prefer clear, testable boundaries over unnecessary abstraction.

## Possible logical layers
- Bootstrap: metadata, loading, dependency checks, lifecycle hooks.
- Business logic: feature rules, separated from presentation where practical.
- WordPress integration: actions, filters, admin UI, REST controllers, blocks, shortcodes, cron jobs.
- Persistence: options, post meta, custom post types, taxonomies or custom tables chosen for actual access patterns.
- Presentation: admin/frontend UI, templates and assets.
- External integrations: API clients with timeouts, validation and error handling.

These are options, not mandatory folders for every project.

## Naming and lifecycle
- Use a unique vendor prefix or PHP namespace.
- Prefix global functions, constants, options, transients, cron hooks, asset handles and custom public identifiers.
- Keep hooks and file inclusion predictable; avoid side effects merely from including a file.
- Activation should be short and safe. Deactivation should clean up plugin-owned scheduled work when appropriate.
- Do not delete user data on deactivation. Document uninstall and retention behavior.
- Use versioned, safe migrations when a custom schema is justified.

## Storage and themes
Prefer native WordPress storage when it fits. Justify custom tables with query volume, relationships, indexes, retention and migration needs.
Separate presentation from functionality that must survive a theme switch. For block themes, consider `theme.json`, templates, template parts and patterns. For classic themes, follow the template hierarchy and enqueue assets properly.
