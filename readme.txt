=== XCache Object Cache Backend ===
Contributors: pierreschmitz
Donate link: https://pierre-schmitz.com
Stable tag: 1.1.2
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Requires at least: 3.3.0
Tested up to: 3.6
Tags: xcache, backend, cache, object cache, batcache, performance, speed

An object-cache implementation using the XCache extension.

== Description ==

Using this Plugin WordPress is able to store certain regular used elements into a persistent cache. Instead of computing complex operations over and over again on every single page request, its result is stored in memory once and from then on fetched directly from the cache on future page requests.

Such an object cache will reduce access to your database and speed up page loading.

This implementation uses [XCache](http://xcache.lighttpd.net/)'s variable cache as backend.

== Installation ==

1. You need to install and configure the [XCache PHP extension](http://xcache.lighttpd.net/).
1. Make sure to set a size for the xcache.var_size directive (e.g. `xcache.var_size=64M`).
1. Download and extract the content of the archive file.
1. Upload the file object-cache.php of this plugin into your `/wp-content/` directory. Note that this file needs to be stored directly into your content directory and not under the plugins directory.
1. This plugin should now work without any further configuration. Check if it is listed under `Plugins` -> `Installed Plugins` -> `Drop-ins`.

== Frequently Asked Questions ==

= "XCache is not configured correctly" =
You will see this error message when either the xcache module is not loaded or the `xcache.var_size` directive is not set in your php.ini. If not configured, this setting defaults to 0 which disables the cache.

= "Cannot redeclare wp_cache_add()..." =
This error indicates that you likely have two copies of the object cache installed. Make sure you have put the file object-cache.php into your `/wp-content/` directory only. Do not upload it to the `/wp-content/plugins` direcotry or any subdirectory like `/wp-content/plugins/xcache`. The `XCache Object Cache Backend` is not a regular WordPress plugin but a `Drop-in`. Terefore you cannot store it into the `plugins` direcotry.

== Changelog ==

= 1.1.2 =
* Fix wrong logic when calling flush()
* Verify compatibility with WordPress 3.6

= 1.1.1 =
* Check if the variable cache is correctly configured and enabled
* Clarify the installation instructions
* added answers to "Frequently Asked Questions"

= 1.1.0 =
* Compatibility with WordPress 3.5 API

= 1.0.3 =
* Compatibility with XCache < 1.3 which does not have the xcache_unset_by_prefix function

= 1.0.2 =
* Compatibility with WordPress 3.4 API

= 1.0.1 =
* Compatibility with [Batcache](http://wordpress.org/extend/plugins/batcache/)

= 1.0.0 =
* initial version
