.. raw:: html

    <style> .red {color:red} </style>

Woocommerce
=============

Authentication will be supported by the main plugin (Integrate Firebase PRO). The other features will come as an extension plugin. 

If you have any requests please create a `ticket <https://github.com/dalenguyen/firebase-wordpress-plugin/issues>`_ for it.

Authentication (PRO)
----------------------------------

The authentication process from Woocommerce can be overridden by the Integrate Firebase PRO plugin. Below is the example configuration of **Woocommerce Account & Privacy.**

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

The first iteration of the extension is to sync order and product to firebase (realtime / firestore). After successfully purchase, the order will be synced to firebase. 

The purpose of syncing Orders & Products is to have the flexibility of assigning user roles / permissions based on their purchases - this can be done via custom cloud functions.

The configuration is straight forward, after installing the plugin, you will have to pick the right type of database and the name for the database in order to save the Woocommerce's order.

.. figure:: /images/extensions/woocommerce/woo-configuration.png
    :scale: 70%
    :align: center

    Extension configuration

Since v2.0.0, when you delete a product in WooCommerce, it will also delete in Firebase. Product data model will also base on WooCommerce Rest API structure. The existing product structure will be Deprecated in the next few releases - please modify your code in order to avoid breaking.

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

.. role:: red

Product data structure is based on `WooCommerce Product API <https://woocommerce.github.io/woocommerce-rest-api-docs/#products>`_. :red:`If you haven't updated your code to match with the new Product data structure, please do so. The existing structure will be deprecated in the next release`.

If you enter the collection name for product in the settings, the WooCommerce product will be synced to Realtime / Firestore. This schema for product is based on WooCommerce Product API.

Synced Membership -> Firebase (Extension)
----------------------------------

First, you need to set the collections name for the `memberships` in Firebase. Then when an order is purchased or somebody edits the membership, it will be updated to firebase. 

.. figure:: /images/extensions/woocommerce/membership.png
    :scale: 70%
    :align: center

    Membership model

Synced Subscriptions -> Firebase (Extension - v2.2.0)
----------------------------------

Similar to Membership, this extension will sync `Woocommerce Subscriptions <https://woocommerce.com/products/woocommerce-subscriptions/>`_ to Firebase. 

It happens after a Subscription status is saved / changed.

Video: `Create & Save WooCommerce Subscriptions to Firebase <https://www.youtube.com/watch?v=CKJkWiWTdzQ&list=PLchk3ZdnnL-bngknCj7dMQQ6JmAfSdxd8&index=1&ab_channel=TechCater>`_

Create Firebase User after Checkout (Extension - v2.17.0)
----------------------------------

This feature allows users to have their users synced to Firebase after checkout process. 

First, you need to enable the feature in the WooCommerce settings.

.. figure:: /images/extensions/woocommerce/woo-send-password-setting.png
    :scale: 70%
    :align: center

    Enable send password setup link in WooCommerce settings

After that, update Firebase Woocommerce settings.

.. figure:: /images/extensions/woocommerce/woo-new-account-password.png
    :scale: 70%
    :align: center

    Firebase Woocommerce New Account Password settings

After that, when a user resets their password by clicking the link in the email, the user will be created in Firebase.

.. figure:: /images/extensions/woocommerce/woo-set-new-password-email.png
    :scale: 70%
    :align: center

    Set new password email

Then users can login with their email and password in either Firebase or WordPress.

Synced Product Firebase -> WordPress (Extension)
----------------------------------

This ability is in beta, and if you want to test this one out. Please create a ticket or send and email to me for discussing.

This is not the end, the extension will continue to grow. So please add your feature request on `Github <https://github.com/dalenguyen/firebase-wordpress-plugin>`_.