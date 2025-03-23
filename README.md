# Display Builder

[Drupal module display builder](https://www.drupal.org/project/display_builder)

A display building tool by the UI Suite team:

- Design system native: fully use your design system (components, style utilities, icons, themes/modes, CSS variables...) directly in Drupal without the burden of compatibility layers
- Unified: can be used instead of Layout Builder for entity view displays, Block Layout for page displays, and as a replacement of the Views' display building feature.
- Modern: A builder for the world of today, with powerful features (dynamic previews, pattern presets, real-time collaboration, deep integration with Drupal APIs...)

## Installation

For now Display Builder works only in dev mode and poorly with Drupal cache.

It must be tested only with:

- **NO JS aggregation** (will fail Data from a field on entity view)

Other settings like performance or development settings can be production oriented.

_Note_: Enabling your component based theme before enabling Display Builder will help load fixtures.

### If re-install

We use `localStorage` that can change anytime, be sure to clear your local storage on each new install to start fresh.

On your browser > developer toolbar > Application > Local storage > Delete all or clear all.

### Page Layout specifics

If testing `display_builder_page_layout`, first set the theme before enable to allow a fixture to be loaded.

Disable ALL blocks from block layout page (/admin/structure/block) and **KEEP** only: Help and Main page content.

### Patches in composer.json

- <https://drupal.org/i/3191847>
- <https://drupal.org/i/3438993>

```json
        "patches": {
            "drupal/core": {
                "Enable _theme key in *.routing.yml options": "https://www.drupal.org/files/issues/2021-08-03/3191847-9.patch"
            },
            "drupal/page_manager": {
                "Some mandatory parameters are missing": "https://www.drupal.org/files/issues/2024-08-14/page-manager-3438993-MR34-24.patch"
            }
        },
```

### Local libraries

From this folder run:

```shell
npm install
```

### Emergencies

In case of a failing display builder configuration or instance:

- Enable module `display_builder_devel`
- Go to Structure > Display Builder > Devel
- Delete or reset the instance (Reset is in the operations)
