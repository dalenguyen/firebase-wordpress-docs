Woocommerce
=============

Authentication will be supported by the main plugin (Integrate Firebase PRO). The other features will come as an extension plugin. 

If you have any requests please create a `ticket <https://github.com/dalenguyen/firebase-wordpress-plugin/issues>`_ for it.

Authentication (PRO)
----------------------------------

The authention process from Woocommerce can be overrided by the Integrate Firebase PRO plugin. Below is the example configuration of **Woocommerce Account & Privacy.**

.. figure:: /images/extensions/woocommerce/woocommerce-account-configuration.png
    :scale: 70%
    :align: center

    Woocommerce Account configuration

From now, if you use the plugin authentication shortcode, users will be created in WordPress & Firebase at the same time. You can try the process at the `Demo Shop <https://wordpress.dalenguyen.me/product/building-restful-web-apis-with-node-js-express-mongodb-and-typescript/>`_. You can follow to checkout page, the sample product is an abook that I wrote. You don't have to purchase it.

Authentication (Extension)
----------------------------------

The Woocommerce extension supports replacing the default login / register from the `My Account` page with the FirebaseUI Web shortcode.

Demo: https://wordpress.dalenguyen.me/my-account


Synchronization (Extension)
----------------------------------

The first iteration of the extension is to sync order and product to firebase (realtime / firestore). After succesfully purchase, the order will be synced to firebase. 

The purpose of syncing Orders & Products is to have the flexibility of assigning user roles / persmissions based on their purchases - this can be done via custom cloud functions.

The configuration is straight forward, after installing the plugin, you will have to pick the right type of database and the name for the database in order to save the woocommerce's order.

.. figure:: /images/extensions/woocommerce/woo-configuration.png
    :scale: 70%
    :align: center

    Extension configuration

Synced Order -> Firebase (Extension)
----------------------------------

After the purchase is success, the order will be saved to firebase. In this example, it will be saved to realtime database.

.. figure:: /images/extensions/woocommerce/realtime-order-data.png
    :scale: 70%
    :align: center

    Realtime order data

Since v1.8.0, order can be edited directly from WooCommerce and it will be synced to Firebase with line items.

    .. figure:: /images/extensions/woocommerce/line-items.png
        :scale: 70%
        :align: center
    
        Order line items

Synced Product -> Firebase (Extension)
----------------------------------

If you enter the collection name for product in the settings, the WooCommerce product will be synced to Realtime / Firestore. This is the current schema for product in firebase. If you want to extend it, please create a ticket on Github or send email to support.

.. figure:: /images/extensions/woocommerce/firestore-product-data.png
    :scale: 70%
    :align: center

    Firestore product data

Since v1.6.0, you can sync products attributes to Firebase. 

.. figure:: /images/extensions/woocommerce/product-attributes.png
    :scale: 70%
    :align: center

    Products attributes

This is not the end, the extension will continue to grow. So please add your feature request on `Github <https://github.com/dalenguyen/firebase-wordpress-plugin>`_.