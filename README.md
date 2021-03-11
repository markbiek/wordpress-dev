# wordpress-dev

This project is a clone of http://develop.svn.wordpress.org/trunk/ and is essentially the same files that are installed when running `wp scaffold plugin-tests` from the [wp cli](https://developer.wordpress.org/cli/commands/scaffold/plugin-tests/).

## What's Different?

The main difference with this version is that it doesn't delete _any_ data from the test database. This is useful for testing plugins that access large databases where recreating a test database from scratch every time would take too long.

## How Do I Use This?

1. Clone this project somewhere inside your plugin directory
   1. We recommend adding this code to your `.gitignore`
1. Setup your `wp-tests-config.php` file in the `wordpress-dev/trunk` directory
   1. Since no data will be deleted, you can point this at your local development database
1. Copy the sample [phpunit.example.xml](phpunit.example.xml) to `phpunit.xml` in your plugin directory.
1. Copy the sample [bootstrap.example.php](bootstrap.example.php) to `bootstrap.php` in your plugin's `test/` directory.
1. Run `composer require --dev phpunit/phpunit ^7.0` in your plugin directory
   1. (WordPress can't use phpunit >7.4)

Now you're ready to start writing tests! You can run your tests with `./vendor/bin/phpunit` from your plugin directory.
