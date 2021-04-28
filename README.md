# Wordpress & Symfony, with ♥

## Introduction

Use Wordpress 5 as a backend for a Symfony application

The main idea is to use the power of Symfony for the front / webservices with the ease of Wordpress for the backend.


## How does it work ?

When the Wordpress bundle is loaded, it loads a small amount of Wordpress Core files to allow usage of Wordpress functions 
inside Symfony Controllers.

Wordpress is then linked to the bundle via a plugin located in the mu folder.

Because it's a Symfony bundle, there is no theme management in Wordpress and the entire routing is powered by Symfony.


## Features

From Composer :
* Install/update Wordpress via composer
* Install/update plugin via composer

From Symfony :
* Template engine
* Folder structure
* Http Cache
* Routing
* Installation via Composer for Wordpress Core and plugins
* YML configuration ( even for Wordpress )
* DotEnv
* Enhanced Security ( Wordpress is 'hidden' )
* Dynamic image resize

From the bundle itself :
* YML configuration for Wordpress (see bellow )
* Permalink settings for custom post type and taxonomy
* ACF data cleaning
* SF Cache invalidation ( Varnish compatible )
* Post/Image/Menu/Term/User/Comment/Query entities
* Download backup ( uploads + bdd ) from the admin
* Maintenance mode
* Multisite images sync ( for multisite as multilangue )
* SVG Support
* Edit posts button in toolbar on custom post type archive page
* Wordpress predefined routes via permastruct
* Context helpers
* Relative urls
* Terms bugfix ( sort )
* Form helpers ( get / validate / send )
* Multisite post deep copy ( with multisite-language-switcher plugin )
* Image filename clean on upload
* Custom datatable support with view and delete actions in admin
* Extensible, entities, controller and bundle plugins can be extended in the app
* Site health checker
 
 
## Drawbacks

Because of Wordpress design, functions are available in the global namespace, 
it's not perfect but Wordpress will surely change this soon.

Some plugins may not work directly, Woocommerce provider needs some rework 
 
## Demo

A demo is available at https://github.com/wearemetabolism/wordpress-bundle-demo, 

it's an implementation of the Twenty Nineteen theme for Wordpress 5.

## Installation

Make sure Composer is installed globally, as explained in the
[installation chapter](https://getcomposer.org/doc/00-intro.md)
of the Composer documentation.

### Define installation path for Wordpress core and plugins

Edit composer.json and add :

```json
"extra": {
    //...
    "installer-paths": {
        "public/wp-bundle/mu-plugins/{$name}/": ["type:wordpress-muplugin"],
        "public/wp-bundle/plugins/{$name}/": ["type:wordpress-plugin"],
        "public/edition/": ["type:wordpress-core"]
    }
    //...
}
```

### Applications that use Symfony Flex

Open a command console, enter your project directory and execute:

```shell
$ composer require metabolim/wordpress-bundle
```

### Applications that don't use Symfony Flex

### Step 1: Download the Bundle

Open a command console, enter your project directory and execute the
following command to download the latest stable version of this bundle:

```shell
$ composer require metabolim/wordpress-bundle
```

### Step 2: Enable the Bundle

Then, enable the bundle by adding it to the list of registered bundles
in the `config/bundles.php` file of your project:

```php
// config/bundles.php

return [
    // ...
    \Metabolism\WordpressBundle\WordpressBundle::class => ['all' => true],
];
```

### Step 3: Install and configure Wordpress

Please read the [bundle documentation](docs/index.md) to continue
  
## Why not using Bedrock

Because Bedrock "only" provides a folder organisation with composer dependencies management.
Btw this Bundle comes from years of Bedrock usage + Timber plugin...
       
## Why not using Ekino Wordpress Bundle

The philosophy is not the same, Ekino use Symfony to manipulate Wordpress database.
Plus the last release was in 2015...


## Is Wordpress classic theme bad ?

We don't want to judge anyone, it's more like a code philosophy, once you go Symfony you can't go back.

Plus the security is a requirement for us and Wordpress failed to provide something good because of it's huge usage.

## Roadmap

* Create Symfony recipe
* Provide more samples
* Woo-commerce Provider rework
* Global maintenance mode for multi-site
* Unit tests

## Licence

GNU AFFERO GPL
    
    
## Maintainers

This project is made by Metabolism ( http://metabolism.fr )

Current maintainers:
 * Jérôme Barbato - jerome@metabolism.fr
