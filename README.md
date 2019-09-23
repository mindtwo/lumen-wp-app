# Lumen/WordPress App Container

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]
[![Coverage Status][ico-scrutinizer]][link-scrutinizer]
[![Quality Score][ico-code-quality]][link-code-quality]
[![Total Downloads][ico-downloads]][link-downloads]

This package contains a application file to use the Laravel-Lumen service container with some Laravel components inside of WordPress.

## Install

Via Composer

``` bash
$ composer require mindtwo/lumen-wp-app
```

## Usage

Create a `bootstrap/app.php` file like this:
``` php
<?php

require_once dirname(__DIR__).'/vendor/autoload.php';

(new LumenWpApp\LoadEnvironmentVariables(
    dirname(__DIR__)
))->bootstrap();

/*
|--------------------------------------------------------------------------
| Create The Application
|--------------------------------------------------------------------------
|
| Here we will load the environment and create the application instance
| that serves as the central piece of this framework. We'll use this
| application as an "IoC" container and router for this framework.
|
*/

$app = new LumenWpApp\Application(
    dirname(__DIR__)
);

/*
|--------------------------------------------------------------------------
| Load The Application
|--------------------------------------------------------------------------
*/
$app->configure('app');
$app->configure('cache');
$app->configure('database');
$app->configure('filesystems');
$app->configure('logging');
$app->configure('services');

/*
|--------------------------------------------------------------------------
| Load The Application
|--------------------------------------------------------------------------
*/

return $app;
```

Inside your `wp-config.php` file:
``` php
/** Load Application */
$app = require_once(realpath(__DIR__ . '/../bootstrap/app.php'));
```

Inside your `functions.php` file:
``` php
$app->registerConfiguredProviders()->boot();
```
## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CODE_OF_CONDUCT](CODE_OF_CONDUCT.md) for details.

## Security

If you discover any security related issues, please email info@mindtwo.de instead of using the issue tracker.

## Credits

- [mindtwo GmbH][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/mindtwo/lumen-wp-app.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/mindtwo/lumen-wp-app/master.svg?style=flat-square
[ico-scrutinizer]: https://img.shields.io/scrutinizer/coverage/g/mindtwo/lumen-wp-app.svg?style=flat-square
[ico-code-quality]: https://img.shields.io/scrutinizer/g/mindtwo/lumen-wp-app.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/mindtwo/lumen-wp-app.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/mindtwo/lumen-wp-app
[link-travis]: https://travis-ci.org/mindtwo/lumen-wp-app
[link-scrutinizer]: https://scrutinizer-ci.com/g/mindtwo/lumen-wp-app/code-structure
[link-code-quality]: https://scrutinizer-ci.com/g/mindtwo/lumen-wp-app
[link-downloads]: https://packagist.org/packages/mindtwo/lumen-wp-app
[link-author]: https://github.com/mindtwo
[link-contributors]: ../../contributors
