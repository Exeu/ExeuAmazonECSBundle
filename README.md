Exeu AmazonECS Bundle
===================

## Build Status ##

Travis:

Comming soon..

Jenkins:

[![Build Status](http://ci.pixel-web.org/job/ExeuAmazonECSBundle/badge/icon)](http://ci.pixel-web.org/job/ExeuAmazonECSBundle/)

## Installation

### Symfony 2.0.x

Add the following lines in your `deps` file:

``` ini
[AmazonECSPHPLibrary]
    git=git://github.com/Exeu/Amazon-ECS-PHP-Library.git
    target=amazon_ecs_php_library
[ExeuAmazonECSBundle]
    git=git://github.com/Exeu/ExeuAmazonECSBundle.git
    target=bundles/Exeu/AmazonECSBundle
```

Modify the autoload.php:

``` php
<?php

// app/autoload.php
$loader->registerNamespaces(array(
    // ...
    'Exeu'              => __DIR__.'/../vendor/bundles',
    // ...
));

require __DIR__.'/../vendor/amazon_ecs_php_library/lib/AmazonECS.class.php';
```

Now run the vendors script:

``` bash
$ php bin/vendors install
```

### Symfony 2.1.x

Add ExeuAmazonECSBundle in your composer.json:

```js
{
    "require": {
        "exeu/amazon-ecs-bundle": "dev-master"
    }
}
```

Now tell composer to download the bundle by running the command:

``` bash
$ php composer.phar update exeu/amazon-ecs-bundle
```

Dont forget to activate the bundle in your AppKernel:

``` php
<?php

// in AppKernel::registerBundles()
$bundles = array(
    // ...
    new Exeu\AmazonECSBundle\ExeuAmazonECSBundle(),
    // ...
);

```

## Configuration

To get this bundle working you have to add the following to your config.yml

``` yaml
# app/config/config.yml

exeu_amazon_ecs:
    access_key: YOUR_ACCESS_KEY
    secret_key: YOUR_SECRET_KEY
    country: COUNTRY CODE
    associate_tag: YOUR_ASSOCIATE_TAG
```

## Usage ##

To work with the Amazon Product Advertising API you need to get the new service for example in your controller:

``` php
<?php

$amazonEcs = $this->get('exeu_amazon_ecs.pa');

```

Now you can execute your first searchrequest:

``` php
<?php

// ...
$result = $amazonEcs->category('Blended')->search('PHP 5');

var_dump($result);

```

For more detailed information See: [Amazon-ECS-PHP-Library - Examples](https://github.com/Exeu/Amazon-ECS-PHP-Library/tree/master/samples) )