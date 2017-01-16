[![Latest Stable Version](https://poser.pugx.org/renedekat/laravel-view-finder-creater/v/stable)](https://packagist.org/packages/renedekat/laravel-view-finder-creater)
[![Total Downloads](https://poser.pugx.org/renedekat/laravel-view-finder-creater/downloads)](https://packagist.org/packages/renedekat/laravel-view-finder-creater)
[![Latest Unstable Version](https://poser.pugx.org/renedekat/laravel-view-finder-creater/v/unstable)](https://packagist.org/packages/renedekat/laravel-view-finder-creater)
[![License](https://poser.pugx.org/renedekat/laravel-view-finder-creater/license)](https://packagist.org/packages/renedekat/laravel-view-finder-creater)
[![composer.lock](https://poser.pugx.org/renedekat/laravel-view-finder-creater/composerlock)](https://packagist.org/packages/renedekat/laravel-view-finder-creater)

[![Build Status](https://scrutinizer-ci.com/g/renedekat/laravel-view-finder-creater/badges/build.png?b=master)](https://scrutinizer-ci.com/g/renedekat/laravel-view-finder-creater/build-status/master)
[![StyleCI](https://styleci.io/repos/79127109/shield?branch=master)](https://styleci.io/repos/79127109)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/renedekat/laravel-view-finder-creater/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/renedekat/laravel-view-finder-creater/?branch=master)
[![SensioLabsInsight](https://insight.sensiolabs.com/projects/a531fbe1-9636-4ced-bd3d-1144c712540f/mini.png)](https://insight.sensiolabs.com/projects/a531fbe1-9636-4ced-bd3d-1144c712540f)

# Laravel View Finder that creates missing view files


By default Laravel throws an error when a view file cannot be found. This package replaces the default view finder,
and creates your missing view files on the fly, based on a template.

The default template can be found in resources/assets/pages/missing.blade.php after you've published it.


## Installation

Via Composer

``` bash
$ composer require renedekat/laravel-view-finder-creater --sort-packages
```

Replace the default ViewServiceProvider 

```php
// config/app.php
'providers' => [
	...
	//Illuminate\View\ViewServiceProvider::class,
	ReneDeKat\LaravelViewFileFinder\ViewServiceProvider::class,
];
``` 

Or, if you only want to use it locally (handy during development)

```php
// config/app.php
'providers' => [
	...
	//Illuminate\View\ViewServiceProvider::class,
];
```

```php
// app/Providers/AppServiceProvider
public function register()
{
    ...
    if ('local' == $this->app->environment()) {
        $this->app->register(\ReneDeKat\LaravelViewFileFinder\ViewServiceProvider::class);
    } else {
        $this->app->register(\Illuminate\View\ViewServiceProvider::class);
    }
    ...
}
```

The missing page template file must be published with this command:

```bash
php artisan vendor:publish --provider="ReneDeKat\LaravelViewFileFinder\ViewServiceProvider" --tag="assets"
```

It will be published in `resources/assets/pages/missing.blade.php`


## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email renedekat@9lives-development.com instead of using the issue tracker.

## Credits

- [René de Kat][https://github.com/renedekat]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
