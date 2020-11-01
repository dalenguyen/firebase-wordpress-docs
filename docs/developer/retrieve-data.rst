Retrieve Data and Display on WordPress
=============

This guide will help to retrieve the data from Firestore and display on WordPress. I should the same with Realtime Database. Please follow the guide from Firebase official documentation.

Step 1: Create a custom shortcode
----------------------------------

You can do this by edit functions.php in your current theme

.. code-block:: php

    // functions.php

    // custom firebase short code 
    function custom_firebase_func($atts)
    {
        return "<div id='custom-firebase'>Test</div>";
    }
    add_shortcode('custom_firebase', 'custom_firebase_func');

Add the shortcode on a page or post

.. figure:: /images/firestore/custom-firebase-shortcode.png
    :scale: 70%
    :align: center

    Custom Firebase Shortcode

.. figure:: /images/firestore/custom-firebase-shortcode-frontend.png
    :scale: 70%
    :align: center

    Custom Firebase Shortcode Frontend

Step 2: Retrieve and display data from Firestore
----------------------------------

Now, it’s all about JavaScript. You can customize, modify and do whatever you want.

.. code-block:: javascript

    (function ($) {
        'use strict';
        $(document).ready(function () {
            const showFirestoreDatabase = () => {
                const db = firebase.firestore();
                const firestoreEl = jQuery('#custom-firebase');

                // You can get the collectionName and documentName from the shortcode attribute
                const collectionName = 'users';
                const documentName = 'document-1'

                if (collectionName && documentName) {
                    const docRef = db.collection(collectionName).doc(documentName);

                    docRef.get().then(doc => {
                        if (doc.exists) {
                            // console.log('Document data:', doc.data());
                            let html = '<table>';
                            jQuery.each(doc.data(), function (key, value) {
                                // You can put condition to filter your value
                                // and it won't show on the frontend
                                html += '<tr>';
                                html += `<td> ${String(key)} </td>`;
                                html += '<td>' + value + '</td>';
                                html += '</tr>';
                            })
                            html += '</table>';
                            firestoreEl.append(html)
                        } else {
                            // doc.data() will be undefined in this case
                            console.error('Please check your collection and document name in the [firestore] shortcode!');
                        }
                    }).catch(error => {
                        console.error('Please check your collection and document name in the [firestore] shortcode!', error);
                    });
                } else {
                    console.warn('Please check your collection and document name in the [firestore] shortcode!');
                }
            }

            showFirestoreDatabase()
        })
    })(jQuery)

Check the code on the WordPress post.

.. figure:: /images/firestore/firestore-on-frontend.png
    :scale: 70%
    :align: center

    Firestore data retrieved

Yay, firestore data is retrieved