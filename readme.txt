=== Plugin Name ===
Contributors: alanstorm
Donate link: http://alanstorm.com/pulse_storm_launcher_for_wordpress
Tags: admin, ajax, posts, plugin, navigation
Requires at least: 4.5.3
Tested up to: 4.7
Stable tag: 1.0.3
License: MIT
License URI: https://opensource.org/licenses/MIT

The Pulse Storm Launcher is an admin launcher application, providing navigation-less access to all your admin pages and posts, including support for products and orders in popular Wordpress e-commerce packages like WooCommerce and WP eCommerce.

== Description ==

The Pulse Storm Launcher is an admin launcher application, providing navigation-less access to all your admin pages and posts, including support for products and orders in popular Wordpress e-commerce packages like WooCommerce and WP eCommerce.

Still not sure what we're about?  Watch our [4 minutes introductory screencast](https://vimeo.com/178378720) where all is revealed. 

== Installation ==

The Pulse Storm Launcher uses WordPress's standard installation workflow.  Just navigate to `Plugins -> Add New`, enter "Pulse Storm" in the search field, press return, and then click the install button. 

If you're more a "install from source type", we maintain a GitHub repository [with the launcher source](https://github.com/astorm/pulsestorm-launcher-wordpress).  Just drop the source in 

    wp-content/plugins/pulsestorm_launcher 
    
and you'll be good to go. 

Once installed

1. Activate the plugin through the 'Plugins' screen in WordPress
2. Use the Settings->Plugin Name screen to configure the plugin's keyboard shortcut
3. Use the plugin by clicking the "Pulse Storm Launcher" link in the admin bar, or invoking the keyboard  shortcut (Ctrl-M by default)


== Frequently Asked Questions ==

= Why would I want this? =

If you, your writers, or your support staff are tired of clicking around the Wordpress admin looking for things. 

= Is this the same Pulse Storm Launcher available for Magento? =

[Yup](https://www.magentocommerce.com/magento-connect/pulse-storm-launcher.html).

== Screenshots ==

1. The Pulse Storm Launcher, searching for WooCommerce Ninjas
2. The Pulse Storm Launcher, having a boring settings screen

== Changelog ==

= 1.0.3 =
* Fix for Warnings on Appearance -> Menu pages
* 4.7 compatability check

= 1.0.2 =
* Fix for breaking Appearance -> Customizations

= 1.0.1 =
* Modified plugin source to better match WordPress best practices

= 1.0 =
* Initial Release
* I bet we didn't get something right and we'll need a 1.0.1

== Upgrade Notice ==

= 1.0 =
This version is the first version. Users will want to "upgrade" to this version (i.e. install the plugin) if they're ready for a faster Wordpress admin experience. 

== WordPress Programmer Note ==

End users programmers can use the following filter hooks to add their own menus to the immediate and ajax launcher results. 

    add_filter('pulsestorm_launcher_ajax_menus', function($links){
        return $links;
    });

    add_filter('pulsestorm_launcher_menus', function($links){
        return $links;
    });    

Just add items to the `$links` array (`var_dump($links)` for the current format) and your links will be available.

The launcher will perform a basic text search (via in page javascript) for items in the immediate array (the `pulsestorm_launcher_menus` hook). Programmers should use the immediate results sparingly, as they're loaded into memory on every page load. 

In the ajax results (the `pulsestorm_launcher_ajax_menus` hook), programmers should use the `terms` request variable to perform a search for their information, and only return links that are relevant.

See `pulsestorm_launcher.php` for more usage tips/hints.  The launcher plugin code uses these hooks internally. 