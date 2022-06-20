# Website Absolwenci

## Notes for (whom?)

### Runtime Requirements

PHP>=8.0 is required and some extensions as required by drupal.

## Notes for developers

### Development requirements

- [docker](https://docker.com)
- [ddev-local](https://ddev.readthedocs.io/)

### Initial preparations

After you've just cloned

```shell
bin/phive install
bin/composer up
```

### Running the website ddev

```shell
ddev start
```

### Executing drush commands

```shell
ddev drush ...
```

The website shall appear under ``https://meil.ddev.site``.
You may customize ddev settings in .ddev/config.local.yaml.
See [config.yaml documentation](https://ddev.readthedocs.io/en/stable/users/extend/config_yaml/)

### Stopping the website

```shell
ddev stop
```
