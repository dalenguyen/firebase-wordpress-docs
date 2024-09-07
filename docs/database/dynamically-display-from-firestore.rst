Dynamically Display Firestore Data on WordPress
=============

This tutorial will help to retrieve a list of documents from Firestore, then generate a link that leads to a child page. Just imagine this as an blog page and a post page. 

Demo:

- https://wordpress.dalenguyen.me/display-firestore-collection-data/
- https://wordpress.dalenguyen.me/display-firestore-collection-as-blocks/

You need to create two pages:

- Parent page to display a list of documents from Firestore
- Child page to display a single document from the parent page 

The shortcode allows to you to add your custom class for CSS styling. Please add custom CSS in the WordPress for your own styling.

Create the Parent Page
----------------------------------

After you create a new WordPress page, use this shortcode to retrieve data from Firestore and display them. 

.. code-block:: php

    // show firestore data basing on collection name as blocks
    [firestore_blocks class='optional-your-CSS-class-name' collection_name='blog' display_fields='title,description,more' images='url']

    // In order to sort the data, you can add order_by. For example, this will order by title - descendant. You can also combine the orders: `order_by='title|asc,description|desc'`

    // If you want to limit amount of data, you can add limit=<NUMBER>

    // Generate a link to a child page by adding "child_page" & "child_page_target_field"

    [firestore_blocks class='optional-your-CSS-class-name' collection_name='blog' display_fields='title,description,more' images='url' order_by='title|DESC' limit=10 child_page='https://wordpress.dalenguyen.me/dynamic-display-firestore-data-from-blocks' child_page_target_field='title']

    I suggest that you also add this shortcode to show any error when retriving data:
    [firebase_error class='optional-your-CSS-class-name'][/firebase_error]


Create the Child Page
----------------------------------

This page doesn't show anything by itself. It will display data from the parent page. You have to put this shortcode to customize the information that need to be displayed. 

Demo: https://wordpress.dalenguyen.me/dynamic-display-firestore-data-from-blocks?docId=1prQPhET2etbBRkrF3f8

.. code-block:: php

    // Data is generated from https://wordpress.dalenguyen.me/display-firestore-collection-as-blocks
    // document_name will be replace by the docId from query params 

    // E.g. https://wordpress.dalenguyen.me/dynamic-display-firestore-data-from-blocks/?docId=1prQPhET2etbBRkrF3f8

    [firestore class='optional-your-CSS-class-name' collection_name='blog' document_name='from-queries' display_fields='title,description' images='url' display_type='blocks']

After creating two pages, you have a system that can retrieve information from Firestore and display it dynamicly on WordPress. 