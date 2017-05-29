[![Latest Stable Version](https://poser.pugx.org/bentools/cartesian-product/v/stable)](https://packagist.org/packages/bentools/cartesian-product)
[![License](https://poser.pugx.org/bentools/cartesian-product/license)](https://packagist.org/packages/bentools/cartesian-product)
[![Build Status](https://img.shields.io/travis/bpolaszek/cartesian-product/master.svg?style=flat-square)](https://travis-ci.org/bpolaszek/cartesian-product)
[![Coverage Status](https://coveralls.io/repos/github/bpolaszek/cartesian-product/badge.svg?branch=master)](https://coveralls.io/github/bpolaszek/cartesian-product?branch=master)
[![Quality Score](https://img.shields.io/scrutinizer/g/bpolaszek/cartesian-product.svg?style=flat-square)](https://scrutinizer-ci.com/g/bpolaszek/cartesian-product)
[![Total Downloads](https://poser.pugx.org/bentools/cartesian-product/downloads)](https://packagist.org/packages/bentools/cartesian-product)

# Cartesian Product
Provides a simple function to get all combinations from a multi-dimensionnal array.

It has a very light memory footprint since it uses a Generator to create all options.

Example
-------

```php
require_once __DIR__ . '/vendor/autoload.php';

use function BenTools\CartesianProduct\cartesian_product;

$cases = [
    'hair' => [
        'blond',
        'red'
    ],
    'eyes' => [
        'blue',
        'green',
        'brown'
    ]
];

foreach (cartesian_product($cases, true) as $possibility) {
    printf('Hair: %s - Eyes: %s' . PHP_EOL, $possibility['hair'], $possibility['eyes']);
}
```

Output:
```
Hair: blond - Eyes: blue
Hair: blond - Eyes: green
Hair: blond - Eyes: brown
Hair: red - Eyes: blue
Hair: red - Eyes: green
Hair: red - Eyes: brown
```

Array output
------------

Instead of using `foreach` you can dump all possibilities into an array.

```php
print_r(cartesian_product($cases, true)->asArray());
```

Output:
```php
Array
(
    [0] => Array
        (
            [hair] => blond
            [eyes] => blue
        )

    [1] => Array
        (
            [hair] => blond
            [eyes] => green
        )

    [2] => Array
        (
            [hair] => blond
            [eyes] => brown
        )

    [3] => Array
        (
            [hair] => red
            [eyes] => blue
        )

    [4] => Array
        (
            [hair] => red
            [eyes] => green
        )

    [5] => Array
        (
            [hair] => red
            [eyes] => brown
        )

)
```

Installation
------------
```
composer require bentools/cartesian-product
```

Unit tests
----------
```
./vendor/bin/phpunit
```