How to Work With Firebase Custom Claims in WordPress
=============

We already knew how to get and display data to WordPress. What if you want to display data to the user who is admin (through custom claims of course), and display something else to the others or just show nothing.

Using shortcode to display custom data
----------------------------------

Since version 0.5.6, I added a shortcode that helps to display data if users log in and have the right custom claims.

.. code-block:: php

    [firebase_show_with_claims 
        class='css-class-name' 
        claims='admin' 
        message='Custom message'
    ]
        HTML Data With Tags
    [/firebase_show_with_claims]

+ class='css-class-name': custom class that you can add style to the element
+ claims='admin': user's claims
+ message='Custom message': this message will show to invalid user

Using custom code to display custom data
----------------------------------

This is the original code to retrieve and display data.

.. code-block:: javascript

    (function ($) {
        'use strict';
        $(document).ready(function () {
            const showFirestoreDatabase = () => {
                const db = firebase.firestore();
                const firestoreEl = jQuery('#custom-firebase');

                // You can get the collectionName and documentName from the shortcode attribute
                const collectionName = 'users';
                const documentName = ‘document-1'

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
                            console.error('Please check your collection and document name in the [custom_firebase] shortcode!');
                        }
                    }).catch(error => {
                        console.error('Please check your collection and document name in the [custom_firebase] shortcode!', error);
                    });
                } else {
                    console.warn('Please check your collection and document name in the [custom_firebase] shortcode!');
                }
            }

            showFirestoreDatabase()
        })
    })(jQuery)

The **showFirestoreDatabase()** function will display data on WordPress. Now, we will wrap it under custom claims check.

.. code-block:: javascript

    (function ($) {
        'use strict';
        $(document).ready(function () {
            const showFirestoreDatabase = () => {
                ...
            }
            // We won't call the function directly here
            // showFirestoreDatabase()

            const getUserCustomClaims = () => {
                firebase.auth().onAuthStateChanged(function (user) {
                    if (firebase.auth().currentUser) {
                        firebase.auth().currentUser.getIdTokenResult()
                        .then((idTokenResult) => {
                            // Confirm the user is an Admin.
                            if (!!idTokenResult.claims.admin) {
                                // We will call the function here
                                showFirestoreDatabase()                        
                            } else {
                                // Show something else 
                            }
                        })
                        .catch((error) => {
                            console.log(error);
                        });
                    }
                });
            }

            getUserCustomClaims()
        })
    })(jQuery)

After checking the user's custom claims, and make sure that it's admin. Then we will call showFirestoreDatabase() function.

This tutorial doesn't limit to retrieve data from Firestore, you can put any functions or features after checking the custom claims.