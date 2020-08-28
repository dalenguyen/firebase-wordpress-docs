
Sync Data from WordPress to Firebase
=============

Since version 0.9.0, I added some event triggers for syncing data from WordPress to Firebase. The plugin now supports syncing Post & Page from WordPress to Firebase. That means when you add or update a new Post or Page. The content will be updated automatically to Firebase (Realtime / Firestore). 

+ For posts, they locate under **wpPosts** collection name. 
+ For pages, they locate under **wpPages** collection name.
+ For custom post types, they will local under **wpTypeNames** collection name.

1. Setting Up
----------------------------------

Make sure the version of the plugin is at least: v0.9.0. Then you can choose which type of data to sync to Firebase. 

.. figure:: /images/sync/sync-configuration-post.png
    :scale: 70%
    :align: center

    Synchronization configuration

In this example, it will choose Firetore as the database, and every new or update posts will be synced to Firestore. You can choose both Post & Page type. If you created custom post types, you can enter them to Custom Post Types field.


2. Create a Sample Post
----------------------------------

After that, you can create a new post or update an existing one.

.. figure:: /images/sync/new-post-in-wordpress.png
    :scale: 70%
    :align: center

    Create a new post

After you save, the post will be added to Firestore. The document id of the post is also the post id for query purpose.

The collection name in Firebase is generated from the plural version fo the post type in WordPress. For example. 

.. code-block:: php

    Posts       -> wpPosts
    Fancy Cars  -> wpFancyCars
    Fancy_Cars  -> wpFancyCars
    Fancy-Cars  -> wpFancyCars 

.. figure:: /images/sync/post-in-firestore.png
    :scale: 70%
    :align: center

    New post in firestore

For taxonomies, will be saved under a node name `taxonomies`.

.. figure:: /images/sync/sync-post-type-taxonomies.png
    :scale: 70%
    :align: center

    Taxonomies node

For author & custom fields, they will be saved under `author` and `custom_fields` node. Author also contains firebase uid and wordpress uid for futher usage.

.. figure:: /images/sync/author-custom-fields.png
    :scale: 70%
    :align: center

    Taxonomies node

When you update the current post, it will override the data in the firestore to make sure that it always updated.