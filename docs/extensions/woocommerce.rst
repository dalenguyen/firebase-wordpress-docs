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

Synchronization (Extension)
----------------------------------

The first iteration of the extension is to sync order to firebase (realtime / firestore). After succesfully purchase, the order will be synced to firebase. 

The configuration is straight forward, after installing the plugin, you will have to pick the right type of database and the name for the database in order to save the woocommerce's order.

.. figure:: /images/extensions/woocommerce/woo-configuration.png
    :scale: 70%
    :align: center

    Extension configuration

After the purchase is success, the order will be saved to firebase. In this example, it will be saved to realtime database.

.. figure:: /images/extensions/woocommerce/realtime-order-data.png
    :scale: 70%
    :align: center

    Realtime order data

This is not the end, the extension will continue to grow. So please add your feature request on `Github <https://github.com/dalenguyen/firebase-wordpress-plugin>`_.