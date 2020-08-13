# Nextcloud development environment

This docker configuration is *only* intended to be used for development of nextcloud apps.
To do so, the `xdebug` extension of PHP is installed additionally.

## How to setup

Simply clone this repository on you local machine.
When running on linux you might want to uncomment the following line:
```
         - /etc/localtime:/etc/localtime:ro
```
You then just need to call

```
docker-compose up -d
```
This will fire up a nextcloud instance on port `8000` by default.

## How to use

You can install any custom apps in `./volumes/custom_apps`.
How to install an app there you must reference to the official documentation and the documentation of the app.

Additionally, the configuration can be tweaked under `./volumes/config`.

The profiler and tracer of xdebug is set up by default.
To make use of it, you need to set a trigger.
This can be done using e.g. an extension to your browser.
See here for [Chrome](https://chrome.google.com/webstore/detail/xdebug-helper/eadndfjplgieldjbigjakmdgkmoaaaoc) and [Firefox](https://addons.mozilla.org/en-GB/firefox/addon/xdebug-helper-for-firefox/).
The correesponding files will be located in `./volumes/xdebug/traces` and `./volumes/xdebug/profiles`.

The user is called `admin` and has password `admin_pwd` by default.

You might wnat to enable debug mode in Nextcloud:
Go to `./volumes/config/config.php` and insert
```php
  'debug' => true,
```

