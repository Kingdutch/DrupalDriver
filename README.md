<?php

/**
 * @file
 */
?>
[![Build Status](https://github.com/jhedstrom/DrupalDriver/actions/workflows/ci.yml/badge.svg)](https://github.com/jhedstrom/DrupalDriver/actions/workflows/ci.yml)

Provides a collection of light-weight drivers with a common interface for interacting with [Drupal](http://drupal.org). These are generally intended for testing, and are not meant to be API-complete.

[Read the full documentation](http://drupal-drivers.readthedocs.org)

[![Latest Stable Version](https://poser.pugx.org/drupal/drupal-driver/v/stable.svg)](https://packagist.org/packages/drupal/drupal-driver) [![Total Downloads](https://poser.pugx.org/drupal/drupal-driver/downloads.svg)](https://packagist.org/packages/drupal/drupal-driver) [![License](https://poser.pugx.org/drupal/drupal-driver/license.svg)](https://packagist.org/packages/drupal/drupal-driver) [![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/jhedstrom/DrupalDriver/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/jhedstrom/DrupalDriver/?branch=master)

### Drivers

These drivers support Drupal versions 7 and 8.

* Blackbox
* Direct Drupal API bootstrap
* Drush

### Installation

``` json
{
  "require": {
    "drupal/drupal-driver": "~2.0"
  }
}
```

``` bash
$> curl -sS http://getcomposer.org/installer | php
$> php composer.phar install
```

### Usage

``` php
<?php

use Drupal\Driver\DrupalDriver;

require 'vendor/autoload.php';

// Path to Drupal.
$path = './drupal-8';

// Host.
$uri = 'http://d8.devl';

$driver = new DrupalDriver($path, $uri);
$driver->setCoreFromVersion();

// Bootstrap Drupal.
$driver->bootstrap();

// Create a node.
$node = (object) array(
  'type' => 'article',
  'uid' => 1,
  'title' => $driver->getRandom()->name(),
);
$driver->createNode($node);
```

### Release notes
See [CHANGELOG](CHANGELOG.MD).
