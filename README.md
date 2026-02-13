# PHPStan extension for CakePHP 2

PHPStan extensions to help test CakePHP 2 projects with PHPStan

Forked from Tomas Votruba's original fork of this package (which was also a fork
to begin with). This version does some updates to make it operable with PHPStan
2.0+.

## Installation

```shell
composer require tomasvotruba/phpstan-cakephp-2 --dev
```

If you have behavior classes in odd locations (perhaps in a vendor directory) you will need to add those locations to
your configuration. For example:

```yaml
# phpstan.neon
parameters:
    behaviorPaths:
        - vendor/my-vendor/my-plugin/src/Model/Behavior/*.php
```

See `extension.neon` for the default list of behavior locations.[composer.json](composer.json)

<br>

## Features

* Treat behavior methods as extra methods on all models (`$model->behaviorMethod()`)
* Treat controller properties named after model classes as instances of those classes (`$controller->Model`)
* Treat controller properties named after component classes as instances of those classes (`$controller->Component`)
* Treat component properties names after component classes as instances of those classes (`$component->Component`)
* Treat `ClassRegistry::init($className)` as returning an instance of `$className` where possible
