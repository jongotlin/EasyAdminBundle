**❮ NOTE ❯** This bundle releases new versions on a regular basis. Make sure
to update your dependencies frequently to get the latest version.
[Check out the changelog](https://github.com/javiereguiluz/EasyAdminBundle/releases)
to learn about the new features and read the [UPGRADE guide](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/UPGRADE.md).

-----

EasyAdmin
=========

[![Build Status](https://travis-ci.org/javiereguiluz/EasyAdminBundle.svg?branch=master)](https://travis-ci.org/javiereguiluz/EasyAdminBundle)
[![SensioLabsInsight](https://insight.sensiolabs.com/projects/a3bfb8d9-7b2d-47ab-a95f-382af395bd51/mini.png)](https://insight.sensiolabs.com/projects/a3bfb8d9-7b2d-47ab-a95f-382af395bd51)
[![Coverage Status](https://coveralls.io/repos/javiereguiluz/EasyAdminBundle/badge.svg?branch=master)](https://coveralls.io/r/javiereguiluz/EasyAdminBundle?branch=master)
<sup><kbd>**SUPPORTS SYMFONY 2.x and 3.x**</kbd></sup>

<img src="https://raw.githubusercontent.com/javiereguiluz/EasyAdminBundle/master/Resources/doc/images/easyadmin-promo.png" alt="Symfony Backends created with EasyAdmin" align="right" />

EasyAdmin lets you create administration backends for Symfony applications
with unprecedented simplicity.

**Features**

  * **CRUD** operations on Doctrine entities (create, edit, list, delete).
  * Full-text **search**, **pagination** and column **sorting**.
  * Fully **responsive** design (smartphones, tablets and desktops).
  * Translated into tens of languages.
  * **Fast**, **simple** and **smart** where appropriate.

**Requirements**

  * Symfony 2.3+ applications (including Symfony 3).
  * Doctrine ORM entities (Doctrine ODM and Propel not supported).
  * Entities with simple primary keys (composite keys not supported).
  * Entities using inheritance are not supported.

Documentation
-------------

#### Getting Started Guide

  * [Chapter 1 - Installation](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/getting-started/1-installation.md)
  * [Chapter 2 - Your First Backend](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/getting-started/2-first-backend.md)
  * [Chapter 3 - Backend Configuration](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/getting-started/3-backend-configuration.md)
  * [Chapter 4 - Views and Actions](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/getting-started/4-views-and-actions.md)
  * [Chapter 5 - Backend Design Customization](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/getting-started/5-design-customization.md)
  * [Chapter 6 - About this Project](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/getting-started/6-about-this-project.md)

#### Tutorials

  * [Customizing Backend Actions](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/customizing-backend-actions.md)
  * [Customizing AdminController](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/customizing-admin-controller.md)
  * [Advanced Design Customization](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/advanced-design-customization.md)
  * [How to Customize the Main Menu](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/custom-menu.md)
  * [How to Format Dates and Numbers](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/format-date-number.md)
  * [How to Translate the Backend](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/i18n.md)
  * [How to Define Custom Actions](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/custom-actions.md)
  * [How to Use a WYSIWYG Editor](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/wysiwyg-editor.md)
  * [How to Upload Files and Images](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/upload-files-and-images.md)
  * [How to Manage Configuration for Complex Backends](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/complex-backend-config.md)
  * [Tips and Tricks](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/tips-and-tricks.md)
  * [Configuration Reference](https://github.com/javiereguiluz/EasyAdminBundle/blob/master/Resources/doc/tutorials/configuration-reference.md)

> **❮ NOTE ❯** you are reading the documentation of the bundle's **development**
> version. You can also [read the documentation of the latest stable version ➜]
> (https://github.com/javiereguiluz/EasyAdminBundle/tree/v1.11.4/).

#### Demo Application

[easy-admin-demo](https://github.com/javiereguiluz/easy-admin-demo) is a simple
Symfony application created to showcase EasyAdmin features.

Installation
------------

### Step 1: Download the Bundle

```bash
$ composer require javiereguiluz/easyadmin-bundle
```

This command requires you to have Composer installed globally, as explained
in the [Composer documentation](https://getcomposer.org/doc/00-intro.md).

### Step 2: Enable the Bundle

```php
<?php
// app/AppKernel.php

// ...
class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = array(
            // ...
            new JavierEguiluz\Bundle\EasyAdminBundle\EasyAdminBundle(),
        );
    }

    // ...
}
```

### Step 3: Load the Routes of the Bundle

```yaml
# app/config/routing.yml
easy_admin_bundle:
    resource: "@EasyAdminBundle/Controller/"
    type:     annotation
    prefix:   /admin

# ...
```

### Step 4: Prepare the Web Assets of the Bundle

```cli
php app/console assets:install --symlink
```

That's it! Now everything is ready to create your first admin backend.

Your First Backend
------------------

Creating your first backend will take you less than 30 seconds. Let's suppose
that your Symfony application defines three Doctrine ORM entities called
`Product`, `Category` and `User`.

Creating the backend for those entities just require you to add the following
configuration in the `app/config/config.yml` file:

```yaml
# app/config/config.yml
easy_admin:
    entities:
        - AppBundle\Entity\Product
        - AppBundle\Entity\Category
        - AppBundle\Entity\User
```

**Congratulations! You've just created your first fully-featured backend!**
Browse the `/admin` URL in your Symfony application and you'll get access to
the admin backend:

![Default EasyAdmin Backend interface](https://raw.githubusercontent.com/javiereguiluz/EasyAdminBundle/master/Resources/doc/images/easyadmin-default-backend.png)

Creating a backend is that simple because EasyAdmin doesn't generate any code.
All resources are served on-the-fly to ensure an exceptional developer
experience.

Without any further configuration, EasyAdmin guesses the best settings to make
your admin backend look "good enough". This may be acceptable for simple
backends and rapid prototypes, but most of the times, you need to customize
some parts of the backend. Keep reading the rest of the documentation to learn
how to do it.

License
-------

This software is published under the [MIT License](LICENSE.md)
