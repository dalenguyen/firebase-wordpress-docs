Sync User Data From WordPress to Firebase
=============

This is a new feature from v1.14.0 - and please deploy cloud functions for this feature. The User data is synced from WordPress to Firebase is minimal. If you have other requests or cases, please create a ticket in `Github <https://github.com/dalenguyen/firebase-wordpress-plugin/issues>`_.

1. Setting Up
----------------------------------

Make sure that you `deployed cloud functions <https://firebase-wordpress-docs.readthedocs.io/en/latest/intro/cloud-functions-deployment.html>`_ and fill the information in **Firebase Settings > Settings**.

.. figure:: /images/sync/firebase-settings-configuration.png
    :scale: 70%
    :align: center

    Setting Tab Configuration

2. Update Your WordPress Tab
----------------------------------

In this example, I want to sync data to Realtime database under **users** path. If you don't want to sync User data to Firebase, you can leave it empty.

.. figure:: /images/sync/enter-users-collection-name.png
    :scale: 70%
    :align: center

    WordPress Tab Configuration

3. How User Data Is Synced
----------------------------------

User data is synced after the login into WordPress using the plugin shortcode: FirebaseUI Web, Login or Register. The plugin will help to UPDATE data from WordPress to Firebase, it doesn't override your user existing data if the fields are different. 

This is an example of user data from Google login. If you users register via the login with **First Name, Last Name, or Phone Number**, those data will also be synced to Firebase.

.. figure:: /images/sync/users-data-in-realtime.png
    :scale: 70%
    :align: center

    User data in Realtime Database
