=== WP Re-Importer ===
Contributors: DJPaul
Tags: importer, wordpress
Requires at least: 3.5
Tested up to: 3.5
Stable tag: 1.0
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Import content from a WordPress export file. Content that already exist is added as a post revision. Also lets you specify a default parent post.

== Description ==

As a fork of the [standard WordPress Importer plugin (v0.6)](http://wordpress.org/extend/plugins/wordpress-importer/), this importer adds the following features:

* Importing content that already exists will add the new version as a post revision
* A default parent post can be set for content that doesn't have a hierarchy defined in the WordPress export file

If you don't need these features, you should use the [standard WordPress Importer](http://wordpress.org/extend/plugins/wordpress-importer/).

== Installation ==

1. Install via WordPress Plugins administration page.
1. Activate the plugin through the 'Plugins' menu in WordPress
1. Go to the Tools -> Import screen, click on 'WordPress Re-Importer'

== Changelog ==

= 1.0 =
* First version. Forked from version 0.6 of the WordPress Importer plugin.
* Importing content that already exists will add the new version as a post revision
* A default parent post can be set for content that doesn't have a hierarchy defined in the WordPress export file

== Frequently Asked Questions ==

= Help! I'm getting out of memory errors or a blank screen. =
If your exported file is very large, the import script may run into your host's configured memory limit for PHP.

A message like "Fatal error: Allowed memory size of 8388608 bytes exhausted" indicates that the script can't successfully import your XML file under the current PHP memory limit. If you have access to the php.ini file, you can manually increase the limit; if you do not (your WordPress installation is hosted on a shared server, for instance), you might have to break your exported XML file into several smaller pieces and run the import script one at a time.

For those with shared hosting, the best alternative may be to consult hosting support to determine the safest approach for running the import. A host may be willing to temporarily lift the memory limit and/or run the process directly from their end.

-- [WordPress Codex: Importing Content](http://codex.wordpress.org/Importing_Content#Before_Importing)

== Filters ==

The importer has a couple of filters to allow you to completely enable/block certain features:

* `import_allow_create_users`: return false if you only want to allow mapping to existing users
* `import_allow_fetch_attachments`: return false if you do not wish to allow importing and downloading of attachments
* `import_attachment_size_limit`: return an integer value for the maximum file size in bytes to save (default is 0, which is unlimited)

There are also a few actions available to hook into:

* `import_start`: occurs after the export file has been uploaded and author import settings have been chosen
* `import_end`: called after the last output from the importer
