# WordPress Stubs

This package provides stub declarations for [WordPress](https://wordpress.org/) core functions, classes, interfaces, and global variables.  These stubs can help plugin and theme developers leverage static analysis tools like [Psalm](https://getpsalm.org/), which often dislike parsing all of WordPress.

The stubs are generated directly from the [source](https://github.com/johnpbloch/wordpress-core) using [giacocorsiglia/stubs-generator](https://github.com/GiacoCorsiglia/php-stubs-generator).  Needless to say, this library repackages a subset of WordPress code, which is the work of the WordPress core developers.  Granted, it's a useless subset without the real thing!

## Installation

Require this package as a dev-dependency with [Composer](https://getcomposer.org):

```
composer require --dev giacocorsiglia/wordpress-stubs
```

Alternatively, you may download `wordpress-stubs.php` directly.

## Usage with Psalm

Update your Psalm config to include the section:

```xml
<stubs>
    <file name="vendor/giacocorsiglia/wordpress-stubs/wordpress-stubs.php" />
</stubs>
```

Furthermore, ensure WordPress core code is _not_ included under `<projectFiles>`.

## Versioning

This package is versioned to match the WordPress version from which the stubs are generated.

## Generating stubs for a different WordPress version

You should be running PHP 7.1 or later to follow these steps, so any function definitions that are polyfills for older versions of PHP are excluded from the stubs.  Additionally, the Stubs Generator package at least requires PHP 7.1.

1. Clone this repository and `cd` into it.
2. Update `"johnpbloch/wordpress": "X.X.X"` in `composer.json` with your desired version.
3. Run `composer update`
4. Run `./generate.sh`

The `wordpress-stubs.php` file should now be updated.  Feel free to submit a Pull Request if you'd like to see a release for a newer version.
