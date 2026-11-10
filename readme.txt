=== NDV Product Image Upload for WooCommerce ===
Contributors: nowdigiverse
Tags: woocommerce, image upload, product customization, cropping, file upload
Requires at least: 5.9
Tested up to: 7.1
Requires PHP: 7.2
Stable tag: 1.2.0
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Let WooCommerce customers upload and crop images and PDFs on product pages before adding to cart, with per-product rules and secure handling.

== Description ==

NDV Product Image Upload for WooCommerce lets both logged-in customers and guests upload and crop custom images (and PDFs) for specific WooCommerce products before adding them to the cart. It is ideal for personalised products, custom prints, photo gifts, and any store where customers supply their own artwork.

Everything is configured per product, so each product can have its own required file count, file-size limit, allowed file types, button styling, and cropping rules.

= Key Features =

* **Guest & logged-in uploads** — customers can upload without creating an account.
* **Per-product configuration** — set required file count, max file size, allowed types, button text and colour for each product.
* **Built-in cropping** — crop before uploading with Cropper.js, including shape presets (square, rectangle, circle, heart) and fixed aspect ratios.
* **PDF upload support** — accept PDFs alongside images.
* **Resolution validation** — optionally enforce minimum/maximum image dimensions.
* **Lock quantity to 1** — optionally prevent customers from ordering more than one of a product they upload artwork for.
* **Default settings** — define fallback settings used by products without their own configuration.
* **Global controls** — hide express checkout buttons (Apple Pay, Google Pay, PayPal Express) on product pages, and auto-clean uploaded images from completed/cancelled/refunded orders after a chosen number of days.
* **Secure file handling** — uploaded files are validated by type, size and content, stored outside the media library, protected with an `.htaccess` rule on Apache/LiteSpeed, and served through a tokenised endpoint.
* **HPOS compatible** — works with WooCommerce High-Performance Order Storage.
* **Data control** — choose whether to keep or delete plugin data on uninstall.

= Use Cases =

* Custom T-shirts and apparel — customers upload their designs
* Photo products — personalised photo books, mugs, or prints
* Custom artwork and logo printing
* Wedding and event stationery

= Premium version =

A separate **Pro add-on** extends this free plugin with:

* Bulk Operations — apply upload settings to many products at once
* Upload fees — charge a flat fee per item or a price per uploaded image, with a free-image allowance and a live estimate before Add to cart
* Optional uploads — let customers add a product to the cart without uploading, per product or site-wide
* Shortcode — place the upload widget for any product on any page with `[cpiu_upload_widget]`
* Elementor widget — place the upload interface in Elementor templates
* Import / Export — back up and restore all plugin settings as JSON
* Security Logs — monitor upload attempts and security events

The Pro add-on requires this free plugin and is available from the developer at https://www.nowdigiverse.com/products/ndv-image-upload/. The free plugin is fully functional on its own: no feature here needs Pro, a licence key or an account.

== Installation ==

1. Upload the plugin files to `/wp-content/plugins/nowdigiverse-product-image-upload`, or install through the WordPress Plugins screen.
2. Activate the plugin through the 'Plugins' screen in WordPress.
3. Ensure WooCommerce is installed and active.
4. Go to **NDV Image Upload** in the admin menu and configure a product under "Add Configuration".

== Frequently Asked Questions ==

= Does this plugin require WooCommerce? =

Yes. It integrates with WooCommerce products and the cart, and requires WooCommerce to be installed and active.

= Can guests upload without an account? =

Yes. Guests can upload using a temporary session identifier; no account is required.

= What file types are supported? =

JPG, JPEG, PNG, GIF, WEBP and PDF. You can enable or disable types per product.

= Can I set different rules for different products? =

Yes. Each product can have its own required file count, file-size limit, allowed types, button styling, cropping and resolution rules. Products without a configuration use your Default Settings.

= Can I stop customers ordering more than one of an upload product? =

Yes. Enable "Lock quantity to 1" on that product's own configuration. The quantity selector is fixed at 1 on the product page and cart wherever uploads are enabled. (The Default Settings checkbox pre-fills new configurations you create afterwards — it does not retroactively apply to products you've already configured.) If you have already marked a product "Sold individually" in WooCommerce's own product settings, that continues to work as before.

= How are uploads kept secure? =

Every file is validated by type, size and content (including a scan for executable content), filenames are randomised, files are stored in a protected directory, and they are served through a tokenised endpoint. A short cooldown between consecutive guest requests helps deter abuse.

= How do I protect the uploads folder on Nginx? =

Because Nginx ignores `.htaccess`, add this to your server block for strict protection (filenames are already randomised so they cannot be guessed):

`location ^~ /wp-content/uploads/custom_product_images/ { deny all; return 403; }`

= What happens to my data when I uninstall? =

You choose. On the "Uninstall Preferences" tab you can keep all data (default) or delete it on uninstall. Files referenced by orders are preserved either way for data integrity.

== Screenshots ==

1. Admin interface showing per-product configuration
2. Frontend upload interface with the cropping tool
3. Default Settings and Global Settings

== Changelog ==

= 1.2.0 =
* Added: a "Go Pro" tab on the settings page that lists what the separate Pro add-on adds, a "Go Pro" link in the settings header and on the Plugins screen. They are informational only: no free feature is locked, nothing is shown outside this plugin's own screens, and the links disappear once Pro is active.
* Added: `cpiu_show_pro_upsell` filter to hide those links.
* Changed: the readme's Pro feature list now matches the current Pro add-on.

= 1.1.2 =
* Compatibility: tested with WooCommerce 11.2 and WordPress 7.1, including an in-place upgrade from WooCommerce 10.9 with 600 configured products. `WC tested up to` raised from 10.9, so WooCommerce no longer flags the plugin as untested. No code or data changes.

= 1.1.1 =
* Fixed: on the block cart and checkout, a product with no upload configuration could show another product's uploaded files when both were in the cart. Thumbnails now appear only under the product they were uploaded for. Display only: order data was never affected.
* Improved: uploaded-file thumbnails now find their product when its name contains curly quotes, dashes or "&".

= 1.1.0 =
* Added: "Lock quantity to 1" per-product (and default) setting, so customers can't order more than one of a product they upload custom artwork for. Enforced via WooCommerce's own `woocommerce_is_sold_individually` filter, so it never overrides a product already marked "Sold individually".
* Compatibility: confirmed working against WooCommerce 10.9 (full core-flow regression pass); `WC tested up to` raised from 9.5.

= 1.0.0 =
* Initial WordPress.org release.
* Per-product image/PDF upload with a built-in cropper (shapes, aspect ratios, zoom/rotate/flip).
* Guest and logged-in uploads with secure, validated file handling.
* Resolution validation, default settings, and global controls (express-checkout hiding, order-image auto-cleanup).
* HPOS compatibility and uninstall data preferences.

== Upgrade Notice ==

= 1.2.0 =
Adds an informational "Go Pro" tab and links on the plugin's own screens. No changes to uploads, settings or order data.

= 1.1.2 =
Compatibility release: tested with WooCommerce 11.2 and WordPress 7.1. No code or data changes.

= 1.1.1 =
Fixes uploaded-file thumbnails appearing under the wrong product on the block cart and checkout.

= 1.0.0 =
Initial WordPress.org release.

== Privacy Policy ==

This plugin does not send any data to third parties. Uploaded files are stored on your own server. For guests, a temporary session identifier is created to manage uploads; it is cleaned up when sessions expire or orders complete.

During an upload request the visitor's IP address is read from the server and used transiently for rate limiting (a short cooldown between consecutive guest requests). It is not stored permanently and never leaves your server.

== Credits ==

* [Cropper.js](https://github.com/fengyuanchen/cropperjs) (MIT) for image cropping
* [Select2](https://github.com/select2/select2) (MIT) for the admin product search field
* WooCommerce for the e-commerce framework
