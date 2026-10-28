# NDV Product Image Upload for WooCommerce

[![WordPress.org plugin version](https://img.shields.io/wordpress/plugin/v/nowdigiverse-product-image-upload)](https://wordpress.org/plugins/nowdigiverse-product-image-upload/)
[![WordPress.org active installs](https://img.shields.io/wordpress/plugin/installs/nowdigiverse-product-image-upload)](https://wordpress.org/plugins/nowdigiverse-product-image-upload/)
[![License: GPL v2 or later](https://img.shields.io/badge/license-GPLv2%2B-blue)](LICENSE)

**NDV Product Image Upload for WooCommerce** is a free WordPress plugin that lets customers **upload and crop images and PDFs on WooCommerce product pages before add to cart**. Guests can upload without an account, and every product gets its own **per-product rules**: required file count, file-size limit, allowed file types, image resolution and cropping shape or aspect ratio. It suits personalised products, custom prints, photo gifts and any store where customers supply their own artwork.

**[Download free on WordPress.org →](https://wordpress.org/plugins/nowdigiverse-product-image-upload/)** · A [Nowdigiverse](https://nowdigiverse.com/) product

## Features

- **Guest and logged-in uploads.** Customers can upload without creating an account.
- **Per-product configuration.** Set the required file count, max file size, allowed types, button text and button colour for each product.
- **Built-in cropping.** Crop before uploading with Cropper.js, including shape presets (square, rectangle, circle, heart) and fixed aspect ratios.
- **PDF upload support.** Accept PDFs alongside images.
- **Resolution validation.** Optionally enforce minimum and maximum image dimensions.
- **Lock quantity to 1.** Optionally stop customers ordering more than one of a product they upload artwork for.
- **Default settings.** Fallback settings for products without their own configuration.
- **Global controls.** Hide express checkout buttons (Apple Pay, Google Pay, PayPal Express) on product pages, and auto-clean uploaded images from completed, cancelled or refunded orders after a chosen number of days.
- **Secure file handling.** Files are validated by type, size and content, stored outside the media library, protected with an `.htaccess` rule on Apache/LiteSpeed, and served through a tokenised endpoint.
- **HPOS compatible.** Works with WooCommerce High-Performance Order Storage.
- **Data control.** Choose whether to keep or delete plugin data on uninstall.

**Use cases:** custom T-shirts and apparel, photo products (photo books, mugs, prints), custom artwork and logo printing, wedding and event stationery.

## Screenshots

Screenshots are hosted on WordPress.org.

| Per-product configuration | Upload interface with cropping | Default and Global Settings |
|---|---|---|
| ![Admin interface showing per-product configuration](https://ps.w.org/nowdigiverse-product-image-upload/assets/screenshot-1.png) | ![Frontend upload interface with the cropping tool](https://ps.w.org/nowdigiverse-product-image-upload/assets/screenshot-2.png) | ![Default Settings and Global Settings](https://ps.w.org/nowdigiverse-product-image-upload/assets/screenshot-3.png) |

## Installation

1. Install from **Plugins → Add New** in WordPress (search for "NDV Product Image Upload"), or upload the plugin files to `/wp-content/plugins/nowdigiverse-product-image-upload`.
2. Activate the plugin on the **Plugins** screen.
3. Make sure WooCommerce is installed and active.
4. Go to **NDV Image Upload** in the admin menu and configure a product under **Add Configuration**.

**Requirements:** WordPress 5.9+, PHP 7.2+, WooCommerce.

## FAQ

**Does this plugin require WooCommerce?**
Yes. It integrates with WooCommerce products and the cart.

**Can guests upload without an account?**
Yes. Guests upload with a temporary session identifier; no account is needed.

**What file types are supported?**
JPG, JPEG, PNG, GIF, WEBP and PDF. You can enable or disable types per product.

**Can I set different rules for different products?**
Yes. Each product can have its own file count, file-size limit, allowed types, button styling, cropping and resolution rules. Products without a configuration use your Default Settings.

**How are uploads kept secure?**
Every file is validated by type, size and content (including a scan for executable content), filenames are randomised, files are stored in a protected directory and served through a tokenised endpoint. A short cooldown between consecutive guest requests helps deter abuse.

**How do I protect the uploads folder on Nginx?**
Nginx ignores `.htaccess`, so add this to your server block:

```nginx
location ^~ /wp-content/uploads/custom_product_images/ { deny all; return 403; }
```

**What happens to my data when I uninstall?**
You choose on the **Uninstall Preferences** tab: keep all data (default) or delete it. Files referenced by orders are preserved either way.

More answers on the [WordPress.org FAQ](https://wordpress.org/plugins/nowdigiverse-product-image-upload/#faq).

## How it compares

| | NDV Product Image Upload | Customer Upload Files for WooCommerce | WooCommerce Product Add-Ons |
|---|---|---|---|
| Price | Free | Paid | Paid |
| Where to get it | [WordPress.org](https://wordpress.org/plugins/nowdigiverse-product-image-upload/) | WooCommerce.com | WooCommerce.com |
| Focus | Customer image and PDF uploads with in-browser cropping (shapes, aspect ratios) and per-product rules | General file uploads | Product add-on fields, including a file-upload field |

Product names are trademarks of their owners; listed for comparison only.

## Pro add-on

A separate, paid Pro add-on extends the free plugin with bulk operations, JSON import/export of settings, a security logs dashboard, an Elementor widget for the upload interface, and per-upload pricing and fees. It is available from [nowdigiverse.com](https://nowdigiverse.com/). The free plugin is fully functional on its own.

## Privacy

The plugin does not send any data to third parties. Uploaded files are stored on your own server. A visitor's IP address is used transiently for rate limiting during an upload request and is not stored permanently.

## Credits

- [Cropper.js](https://github.com/fengyuanchen/cropperjs) (MIT) for image cropping
- [Select2](https://github.com/select2/select2) (MIT) for the admin product search field

## License

[GPLv2 or later](LICENSE). © Nowdigiverse.
