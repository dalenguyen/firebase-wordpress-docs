Display Firestore with Pagination in WordPress
=============

In this tutorial, I will show you how to retrieve the database from your Firestore and display it on the WordPress website with pagination. Before that, make sure you have:

- Install and active Integrate Firebase plugin
- Update the firebase configuration on the Firebase dashboard
- Make sure that Firebase security rules allow you to access the document with or without logging in

The plugin support getting one document and display on the frontend as a table with the shortcode. 

.. code-block:: php

    [firestore_pagination 
        class='test' 
        collection_name='users' 
        display_fields='firstName,lastName,email' 
        order_by='createdAt|DESC' 
        limit="4" child_page='https://wordpress.dalenguyen.me/dynamic-display-firestore-data-from-table/' 
        child_page_target_field='firstName' 
        pagination="true"
    ]

.. figure:: /images/database/firestore-with-pagination.png
    :scale: 70%
    :align: center

    Display firestore with pagination

If the default shortcode doesn't suite your needs, you can create a custom one. Please follow the guide for developers.