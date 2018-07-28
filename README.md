# Shorty

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Total Downloads][ico-downloads]][link-downloads]

Google Url Shortener API Package for Laravel 5.*. Library to shorten URLs, expand URLs, and get stats for shortened URLs. e.g. **goo.gl/XXXXX**

## Installation

To install, run the following in your project directory

``` bash
$ composer require mbarwick83/shorty
```

#### Laravel < 5.5 
Then in `config/app.php` add the following to the `providers` array:

```
Mbarwick83\Shorty\ShortyServiceProvider::class
```

Also in `config/app.php`, add the Facade class to the `aliases` array:

```
'Shorty'    => Mbarwick83\Shorty\Facades\Shorty::class
```

#### Laravel >= 5.5

There is no need to modify `config/app.php` since the provider and alias will be picked up through auto discover.

## Configuration

To publish Shorty's configuration file, run the following `vendor:publish` command:

```
php artisan vendor:publish --provider="Mbarwick83\Shorty\ShortyServiceProvider"
```

This will create a shorty.php in your config directory. Here you **must** enter your Google Shortener URL API Key. Get an API key at [https://developers.google.com/url-shortener/v1/getting_started#APIKey](https://developers.google.com/url-shortener/v1/getting_started#APIKey).

## Usage

**Be sure to include the namespace for the class wherever you plan to use this library**

```
use Mbarwick83\Shorty\Facades\Shorty;
```

#####To shorten a URL:

``` php
$url = "http://google.com";

Shorty::shorten($url);

// returns, http://goo.gl/XXXXX
```

#####To expand a shortened URL:

``` php
$url = "http://goo.gl/XXXXX";

Shorty::expand($url);

// returns, http://google.com
```

#####To get stats on shortened URL:

``` php
$url = "http://goo.gl/XXXXX";

Shorty::stats($url);
```

*If successful, stats response will return:*

```
{
 "kind": "urlshortener#url",
 "id": "http://goo.gl/fbsS",
 "longUrl": "http://www.google.com/",
 "status": "OK",
 "created": "2009-12-13T07:22:55.000+00:00",
 "analytics": {
  "allTime": {
   "shortUrlClicks": "3227",
   "longUrlClicks": "9358",
   "referrers": [ { "count": "2160", "id": "Unknown/empty" } /* , ... */ ],
   "countries": [ { "count": "1022", "id": "US" } /* , ... */ ],
   "browsers": [ { "count": "1025", "id": "Firefox" } /* , ... */ ],
   "platforms": [ { "count": "2278", "id": "Windows" } /* , ... */ ]
  },
  "month": { /* ... */ },
  "week": { /* ... */ },
  "day": { /* ... */ },
  "twoHours": { /* ... */ }
 }
}
```

## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email :author_email instead of using the issue tracker.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/mbarwick83/shorty.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/mbarwick83/shorty.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/mbarwick83/shorty
[link-downloads]: https://packagist.org/packages/mbarwick83/shorty
[link-author]: https://github.com/mbarwick83
[link-contributors]: ../../contributors
