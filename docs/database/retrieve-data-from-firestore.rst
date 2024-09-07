Retrieve Data from Firestore and Display on WordPress
=============

In this tutorial, I will show you how to retrieve the database from your Firestore and display it on the WordPress website. Before that, make sure you have:

- Install and active Integrate Firebase plugin
- Update the firebase configuration on the Firebase dashboard
- Make sure that Firebase security rules allow you to access the document with or without logging in

The plugin support getting one document and display on the frontend as a table with the shortcode. 

Demo: https://wordpress.dalenguyen.me/display-firestore-collection-with-pagination/

.. code-block:: php

    // Get document id '1' from 'users' collection from realtime database
    [realtime class='optional-your-CSS-class-name' collection_name='users' document_name='1' display_fields='email,displayName,role,uid' ]

    // Get document id '1' from 'users' collection from firestore
    [firestore class='optional-your-CSS-class-name' collection_name='users' document_name='1' display_fields='email,displayName,role,uid']

.. figure:: /images/database/show-database-from-shortcode.png
    :scale: 70%
    :align: center

    Display data from firebase

If the default shortcode doesn't suite your needs, you can create a custom one. Please follow the guide for developers.