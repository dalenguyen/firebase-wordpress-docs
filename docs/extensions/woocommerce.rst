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

This feature is in beta. Cloud Functions watch your Firestore collections and create, update or delete the matching products and categories in WooCommerce.

The functions are in the ``functions/`` folder of the extension plugin.

.. note::

    Since **v2.18.0**, the functions are 2nd gen (Node.js 22) and do not use ``functions.config()``. Google stops deploys that use ``functions.config()`` after **March 31, 2027**. If you deployed an older version, follow `Upgrade from v2.17.0 or older`_.

**Configuration**

1. Copy ``functions/.env.example`` to ``functions/.env`` and set the values:

   .. code-block:: bash

       ENVIRONMENT=production
       WC_PRODUCTS_COLLECTION=products
       WC_CATEGORIES_COLLECTION=categories
       WC_API_URL=https://your-store.example.com

2. Store the WooCommerce REST API keys in Secret Manager:

   .. code-block:: bash

       firebase functions:secrets:set WC_CONSUMER_KEY --project project-id
       firebase functions:secrets:set WC_CONSUMER_SECRET --project project-id

3. Deploy:

   .. code-block:: bash

       cd functions
       npm install
       firebase deploy --only functions:products,functions:categories --project project-id

**Sync rules**

- Create and update in Firestore always sync to WooCommerce.
- Delete syncs only when the document has ``delete_on_wordpress: true``.
- After a sync, the function saves ``id``, ``is_synced_to_wordpress`` and ``synced_to_wordpress_at`` on the document.

Upgrade from v2.17.0 or older
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Who must do this:** only sites that deployed the sync functions (Firebase -> WordPress). If you did not deploy them, do step 1 only.

**What you need:** the `Firebase CLI <https://firebase.google.com/docs/cli>`_ (``npm install -g firebase-tools``), signed in with ``firebase login``, and Node.js 22 on your computer. Replace ``project-id`` with your Firebase project ID in all commands.

**Time:** about 20 minutes. Product sync stops for 2 to 5 minutes during step 6.

1. Update the plugin to v2.18.0.

   a. Download the new zip from your account at https://techcater.com/shop/my-account.
   b. In WordPress, go to **Plugins -> Add New Plugin -> Upload Plugin** and upload the zip.
   c. Click **Replace current with uploaded**. Your plugin settings stay the same.

2. Get the ``functions/`` folder of the new version on your computer. It is in ``wp-content/plugins/integrate-firebase-woocommerce/functions``, or in the zip from step 1. Open a terminal in that folder and run:

   .. code-block:: bash

       npm install

3. Show your old values:

   .. code-block:: bash

       firebase functions:config:get --project project-id

   Each old key has a new name and a new place:

   .. list-table::
       :header-rows: 1

       * - Old ``functions.config()`` key
         - New name
         - Where
       * - ``environment``
         - ``ENVIRONMENT``
         - ``.env``
       * - ``woocommerce.products_collection_name``
         - ``WC_PRODUCTS_COLLECTION``
         - ``.env``
       * - ``woocommerce.categories_collection_name``
         - ``WC_CATEGORIES_COLLECTION``
         - ``.env``
       * - ``woocommerce.api.url``
         - ``WC_API_URL``
         - ``.env``
       * - ``woocommerce.api.consumer_key``
         - ``WC_CONSUMER_KEY``
         - Secret Manager
       * - ``woocommerce.api.consumer_secret``
         - ``WC_CONSUMER_SECRET``
         - Secret Manager

4. Set the new values.

   a. Copy ``.env.example`` to ``.env`` and put in your old values:

      .. code-block:: bash

          ENVIRONMENT=production
          WC_PRODUCTS_COLLECTION=products
          WC_CATEGORIES_COLLECTION=categories
          WC_API_URL=https://your-store.example.com

   b. Store the API keys. Each command asks you to paste the value:

      .. code-block:: bash

          firebase functions:secrets:set WC_CONSUMER_KEY --project project-id
          firebase functions:secrets:set WC_CONSUMER_SECRET --project project-id

5. Check the deploy. This builds and validates, but does not deploy. Fix all errors before you continue:

   .. code-block:: bash

       firebase deploy --only functions:products,functions:categories --project project-id --dry-run

6. Delete the old functions, then deploy the new ones. Firebase cannot upgrade a 1st gen function to 2nd gen in place, so the delete is necessary:

   .. code-block:: bash

       firebase functions:delete products-onWrite categories-onWrite --project project-id
       firebase deploy --only functions:products,functions:categories --project project-id

7. Test: add or edit a product in your Firestore products collection. Make sure the change shows in WooCommerce within 1 minute. If it does not, read the logs:

   .. code-block:: bash

       firebase functions:log --only products-onWrite --project project-id

8. Remove the old config:

   .. code-block:: bash

       firebase functions:config:unset woocommerce environment --project project-id

.. warning::

    You cannot roll back to the old functions. They target Node.js 14, and Google no longer accepts Node.js 14 deploys. Do not skip the dry run in step 5.
