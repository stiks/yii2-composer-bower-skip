<p align="center">
    <a href="https://github.com/yiisoft" target="_blank">
        <img src="https://avatars0.githubusercontent.com/u/993323" height="100px">
    </a>
    <h1 align="center">Yii2 Composer Bower Skip</h1>
    <br>
</p>

A Composer package that allows you to install or update Yii2 without Bower-Asset.

[![Latest Stable Version](https://poser.pugx.org/yidas/yii2-composer-bower-skip/v/stable?format=flat-square)](https://packagist.org/packages/yidas/yii2-composer-bower-skip)
[![Total Downloads](https://poser.pugx.org/yidas/yii2-composer-bower-skip/downloads?format=flat-square)](https://packagist.org/packages/yidas/yii2-composer-bower-skip)
[![Latest Unstable Version](https://poser.pugx.org/yidas/yii2-composer-bower-skip/v/unstable?format=flat-square)](https://packagist.org/packages/yidas/yii2-composer-bower-skip)
[![License](https://poser.pugx.org/yidas/yii2-composer-bower-skip/license?format=flat-square)](https://packagist.org/packages/yidas/yii2-composer-bower-skip)

FEATURES
--------

***1. Prevent the error of Bower packages when using Composer install & update for Yii2***

> Problem 1
>
>   \- yiisoft/yii2 2.0.12 requires bower-asset/jquery 2.2.*@stable | 2.1.*@stable | 1.11.*@stable | 1.12.*@stable -> no matching package found.

***2. Skip Bower packages installation or update, No fxp/composer-asset-plugin needed***

Bower packages are not original Packagist source from Composer, so it will cause error when you install or update Bower without a plugin. After requiring this package, Bower packages will not be required or updated, which you will keep the current version of Bower or even no Bower in the project vendor.

If you are using Yii2 Bower, the recommended way is using [yidas/yii2-bower-asset](https://github.com/yidas/yii2-bower-asset) which could install or update Bower for Yii2 without plugin.

---

INSTALLATION
------------

In Yii2 `composer.json`, require `yidas/yii2-composer-bower-skip` before `yiisoft/yii2`.

Example `composer.json`:
```
"require": {
    "php": ">=5.4.0",
    "yidas/yii2-composer-bower-skip": "~2.0.5",
    "yiisoft/yii2": "~2.0.5",
    "yiisoft/yii2-bootstrap": "~2.0.0"
}
```

After that, you can run `composer update` or `composer install` without handling Bower-Asset.

---

CREATE PROJECT
--------------

If you doesn't has Yii2 project yet, choose one of below ways to create:

### Create Project via Composer

You can use Composer to create Yii2 project by using following package:  

#### [yidas/yii2-app-basic](https://github.com/yidas/yii2-app-basic)

```
composer create-project --prefer-dist yidas/yii2-app-basic
``` 

#### [yidas/yii2-app-advanced](https://github.com/yidas/yii2-app-advanced)
```
composer create-project --prefer-dist yidas/yii2-app-advanced
```

These packages are Yii 2 Application Template with fixed Bower, which including [`yidas/yii2-bower-asset`](https://github.com/yidas/yii2-bower-asset) already.


### Creating Project from Official Site

You could download Yii2 project from official [Archive File](http://www.yiiframework.com/download/), then manally install `yii2-composer-bower-skip` on it by following above instruction.

---

FAQ
---

### Still Stuck when Composer Update

If you still get trouble with Bower after install this package, try to delete `composer.lock` file and make sure the asset plugin is disabled: 

```
composer global remove fxp/composer-asset-plugin
composer update
```

### Git Ignore Problem

You may lose Bower vendor after the project is pushed to Git server then re-install Composer from the clone one, you could check the `.gitignore` file in the root folder, which should except bower vendor:

```
# composer vendor dir
/vendor/*
!/vendor/bower
```

If you want keep whole `vendor` ignored, you could take a look for [yidas/yii2-bower-asset](https://github.com/yidas/yii2-bower-asset) which support auto-install for Bower.

---

LIMITATIONS
-----------

This solution is for the situation that you won't update Bower asset packages, and keep a fixed Bower vendor for development such as using `yii2-debug` and `yii2-gii`, so you need to manually update Bower-Asset if needed.

There are some smooth ways to require or update Bower for Yii2:


### Yii2 Bower Asset Package

[yidas/yii2-bower-asset](https://github.com/yidas/yii2-bower-asset) goals to make Bower install by original composer source. Let you install or update Yii2 as soon as possible via Composer.

You can change to use [yidas/yii2-bower-asset](https://github.com/yidas/yii2-bower-asset) if you still want to update Bower asset.


### Asset-Packagist Solution

Thanks to [Asset-Packagist](https://asset-packagist.org/), you may install Bower smoothly in Yii2 with [new version](https://github.com/yiisoft/yii2-app-basic/commit/fc2ec7dfee9313288171e2fe8a5b80e22c1e1509) since release on Packagist. 

