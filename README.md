# Urlbox/Screenshots


## Capture highly accurate webpage screenshots of any site using Urlbox.io in PHP

<!--[![Latest Version](https://img.shields.io/github/release/spatie/browsershot.svg?style=flat-square)](https://github.com/spatie/browsershot/releases)-->
<!--[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)-->
<!--[![Build Status](https://img.shields.io/travis/spatie/browsershot/master.svg?style=flat-square)](https://travis-ci.org/spatie/browsershot)-->
<!--[![StyleCI](https://styleci.io/repos/19386515/shield?branch=master)](https://styleci.io/repos/19386515)-->
<!--[![SensioLabsInsight](https://img.shields.io/sensiolabs/i/9c1184fb-1edb-41d5-9d30-2620d99447c7.svg?style=flat-square)](https://insight.sensiolabs.com/projects/9c1184fb-1edb-41d5-9d30-2620d99447c7)-->
<!--[![Total Downloads](https://img.shields.io/packagist/dt/spatie/browsershot.svg?style=flat-square)](https://packagist.org/packages/spatie/browsershot)-->


This package uses the [Urlbox.io](https://urlbox.io) screenshot as a service to generate website screenshots.


## Installation

This package can be installed through Composer.

```bash
composer require urlbox/screenshots
```

When using Laravel there is a service provider that you can make use of.

```php

// app/config/app.php

'providers' => [
    '...',
    'Urlbox\RendererProvider'
];
```

## Usage

You will need a [Urlbox](https://urlbox.io) account to use this package. Please signup [here](https://urlbox.io/pricing) and get your API Key and  Secret from the Urlbox dashboard once you have logged in.

Here is a sample call to generate a Urlbox screenshot URL:

```php
    $urlbox = \Urlbox\Renderer::fromCredentials('API_KEY', 'API_SECRET');
    $options['url'] = 'example.com';
    $urlboxUrl = $urlbox->generateUrl($options);
    // $urlboxUrl is now 'https://api.urlbox.io/v1/API_KEY/TOKEN/png?url=example.com'
```

You can now use the result (`$urlboxUrl`) by placing it inside an `<img/>` tag as the `src` parameter. 

When you load the image, a screenshot of example.com will be returned.

The following options can be used:

| Option | Default | Description |
| --- | --- | --- |
| `url` | - | The URL of the website you want to screenshot **(Required)** |
| `width` | 1280 | Viewport width of the browser in pixels |
| `height` | 1024 | Viewport height of the browser in pixels |
| `selector` | - | Take a screenshot of the element that matches this selector |
| `thumb_width` | - | Width in pixels of the generated thumbnail, leave off for full-size screenshot |
| `format` | png | Image format of the resulting screenshot image (`png` or `jpg`)|
| `user_agent` | - | User-Agent string used to emulate a particular client. |
| `cookie` | - | Set a cookie value before taking a screenshot. E.g. OptIn=true. Can be set multiple times to set more than one cookie. |
| `delay` | - | Amount of time to wait in milliseconds before urlbox takes the screenshot |
| `wait_for` | - | Waits for the element specified by this selector to be visible on the page before taking a screenshot |
| `timeout` | 30000 | Amount of time to wait in milliseconds for the website at url to respond |
| `full_page` | false | Specify whether to capture the full-length of the website |
| `flash` | false | Enable the flash plugin for flash using websites |
| `force` | false | Take a fresh screenshot instead of getting a cached version |
| `ttl` | 2592000 (30 days) | Short for 'time to live'. Number of seconds to keep a screenshot in the cache. Note the default is also the maximum value for this option. |
| `quality` | 80 | JPEG only - image quality of resulting screenshot (0-100) |
| `disable_js` | false | Turn off javascript on target url to prevent popups |
| `retina` | false | Take a 'retina' or high definition screenshot equivalent to setting a device pixel ratio of 2.0 or @2x. Please note that retina screenshots will be double the normal dimensions and will normally take slightly longer to process due to the much bigger image size. |
| `click` | - | Element selector that is clicked before taking a screenshot e.g. #clickme would click the element with id="clickme" |
| `hover` | - | Element selector that is hovered before taking a screenshot e.g. #hoverme would hover over the element with id="hoverme" |
| `bg_color` | - | Hex code or css color string. Some websites don't set a body background colour, and will show up as transparent backgrounds with PNG or black when using JPG. Use this setting to set a background colour. If the website explicitly sets a transparent background on the html or body elements, this setting will be overridden. |
| `crop_width` | - | Crop the width of the screenshot to this size in pixels |
| `hide_selector` | - | Hides all elements that match the element selector by setting their style to `display:none !important;`. Useful for hiding popups. |
| `highlight` | - | Word to highlight on the page before capturing a screenshot |
| `highlightfg` | white | Text color of the highlighted word |
| `highlightbg` | red | Background color of the highlighted word |
| `use_s3` | false | Save the screenshot directly to the S3 bucket configured on your account |

## Other implementations

- [Node.js](https://github.com/urlbox-io/urlbox-screenshots-node)

## Contributing

We are open to pull requests.

## Security

If you discover any security related issues, please email services@urlbox.io instead of using the issue tracker.

## About Urlbox
Urlbox is a premium Screenshot as a Service API. It lets you render highly accurate screenshots of webpages and display them anywhere you like. [Urlbox.io](https://urlbox.io).

## License

The MIT License (MIT).


