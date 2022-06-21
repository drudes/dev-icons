# drudes/dev-icons

Development environment for drupal modules:

- ``drupal/icon_bundle_api``,
- ``drupal/icon_bundle_fontawesome``,
- ``drupal/icon_field``.

## Requirements

- PHP>=7.3 as required by drupal.
- [docker](https://docker.com)
- [ddev-local](https://ddev.readthedocs.io/)

## Initial preparations

### Required directory

Before we start cloning, ensure that ``repos`` directory exists

```shell
[ -e repos ] || mkdir repos
```

### Cloning

```shell
(cd repos && git clone git@github.com:drudes/icon_bundle_api.git)
(cd repos && git clone git@github.com:drudes/icon_bundle_fontawesome.git)
(cd repos && git clone git@github.com:drudes/icon_field.git)
git clone git@github.com:drudes/dev-icons.git
cd dev-icons
```

You may need to customize ddev settings in .ddev/config.local.yaml, for example

```shell
echo 'router_http_port: "1080"' >> .ddev/config.local.yaml
```

See [config.yaml documentation](https://ddev.readthedocs.io/en/stable/users/extend/config_yaml/)

## Development workflow

### Initializing project

First, Drupal project and our modules need to be installed locally:

```shell
scripts/install-project
```

This will install Drupal website under ``web/`` directory (note that the
``web/`` directory is ``.gitignore``'d). The website shall be available at
``https://dev-icons.ddev.site``.

The modules being developed get installed automatically under
``web/modules/contrib``. Source code shall be modified there.

### Sending changes back to ``repos``

Once, a piece of the work is done, the changes then can be pushed back to
``../repos/*`` with the script:

```shell
scripts/rsync-to-repositories
```

Then, you may examine each individual repository under ``../repos/*`` and see
what needs to be committed to git, for example:

```
(cd ../repos/icon_bundle_api && git status)
```

### Running tests

```
ddev phpunit
```

### Running psalm for static analysis

```
ddev exec vendor/bin/psalm
```
