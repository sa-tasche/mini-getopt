Mini Getopt (a getopt wrapper)
==============================

Very simple wrapper for `getopt()` function.

[![Latest Stable Version](https://poser.pugx.org/jawira/mini-getopt/v/stable)](https://packagist.org/packages/jawira/mini-getopt)
[![Total Downloads](https://poser.pugx.org/jawira/mini-getopt/downloads)](https://packagist.org/packages/jawira/mini-getopt)
[![Monthly Downloads](https://poser.pugx.org/jawira/mini-getopt/d/monthly)](https://packagist.org/packages/jawira/mini-getopt)
[![License](https://poser.pugx.org/jawira/mini-getopt/license)](https://packagist.org/packages/jawira/mini-getopt)
[![composer.lock](https://poser.pugx.org/jawira/mini-getopt/composerlock)](https://packagist.org/packages/jawira/mini-getopt)
[![PHPPackages Referenced By](http://phppackages.org/p/jawira/mini-getopt/badge/referenced-by.svg)](http://phppackages.org/p/jawira/mini-getopt)
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/jawira/mini-getopt.svg)](http://isitmaintained.com/project/jawira/mini-getopt "Average time to resolve an issue")
[![Percentage of issues still open](http://isitmaintained.com/badge/open/jawira/mini-getopt.svg)](http://isitmaintained.com/project/jawira/mini-getopt "Percentage of issues still open")
[![PDS Skeleton](https://img.shields.io/badge/pds-skeleton-blue.svg?style=flat-square)](https://github.com/php-pds/skeleton)
[![Issues](https://img.shields.io/github/issues/jawira/mini-getopt.svg?label=HuBoard&color=694DC2)](https://huboard.com/jawira/mini-getopt)

Usage
-----

This is only a wrapper, therefore the output from `mini-getopt` is going to be 
the same as `getopt()` function.

1. First you have to configure options you want to use. To do so use the 
following methods:

    - `\Jawira\MiniGetopt\MiniGetopt::addRequired`
    - `\Jawira\MiniGetopt\MiniGetopt::addOptional`
    - `\Jawira\MiniGetopt\MiniGetopt::addNoValue`

2. To retrieve values you have to call one of the following method:

    - `\Jawira\MiniGetopt\MiniGetopt::getopt` returns the same as `getopt()`
    - `\Jawira\MiniGetopt\MiniGetopt::getOption` to get only one value

Examples
--------

PHP code:

```php
// Preparing options
$mg = new \Jawira\MiniGetopt\MiniGetopt();
$mg->addRequired('f', 'format');    // value is required
$mg->addOptional('r', 'retry');     // value is optional
$mg->addOptional('q', '');          // only short option
$mg->addNoValue('v', 'verbose');    // no value
$mg->addNoValue('', 'version');     // only long option

// Calling getopt
var_export($mg->getopt());
```

Executing code:

```php
$ php resources/example.php

array (
)
```

```php
$ php resources/example.php -f=xml

array (
   'f' => 'xml',
)
```

```php
$ php resources/example.php --format=xml -r -v

array (
  'format' => 'xml',
  'r' => false,
  'v' => false,
)
```

```php
$ php resources/example.php -f=json -r=yes -v

array (
    'f' => 'json',
    'r' => 'yes',
    'v' => false,
)
```

```php
$ php resources/example.php --retry -vvv

array (
  'retry' => false,
  'v' => 
  array (
    0 => false,
    1 => false,
    2 => false,
  ),
)
```

```php
$ php resources/example.php --version=banana --invalid

array (
  'version' => false,
)
```

How to install
--------------

```console
$ composer install jawira/mini-getopt
```

Contributing
------------

If you liked this project, ⭐ star it on [GitHub][].

License
-------

This library is licensed under the [MIT license](LICENSE.md).


***

Packages from jawira
--------------------

<dl>

<dt><a href="https://packagist.org/packages/jawira/emoji-catalog">jawira/emoji-catalog</a> (library)</dt>
<dd>Get access to +3000 emojis as class constants.</dd>

<dt><a href="https://packagist.org/packages/jawira/plantuml">jawira/plantuml</a> (library)</dt>
<dd>Provides PlantUML integration: plantuml executable and plantuml.jar</dd>

<dt><a href="https://packagist.org/packages/jawira/plantuml-encoding">jawira/plantuml-encoding</a> (library)</dt>
<dd>PlantUML encoding functions.</dd>

<dt><a href="https://packagist.org/packages/jawira/">more...</a></dt>
</dl>

[Github]: https://github.com/jawira/mini-getopt
