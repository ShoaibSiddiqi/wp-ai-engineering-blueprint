# Starter Plugin Template Notes

This directory is a design guide, not a ready-to-install plugin. Generate a concrete starter only after deciding project slug, namespace, text domain, supported versions, dependencies and build tooling.

Possible structure:
```text
plugin-slug/
├── plugin-slug.php
├── uninstall.php          # only if needed
├── readme.txt             # if distributing via WordPress.org
├── includes/
├── admin/                 # if admin UI exists
├── public/                # if frontend UI exists
├── assets/
├── tests/                 # if test tooling is configured
├── composer.json          # if PHP dependencies/tools are used
├── package.json           # if JS tooling is used
└── phpcs.xml.dist         # if PHPCS is configured
```

Replace placeholders and include only components the project needs. Document all commands and configuration. Do not add abstractions or tools merely because they appear in this example.
