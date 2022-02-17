Add Custom Scripts
=============

This guide will show you how to extend the plugin by adding custom scripts, such as JavaScript. The ability of the plugin doesn't limit in the plugin itself. You have totally control of the **`firebase`** object.

If you want to a quick solution, you can try the `template plugin <https://github.com/dalenguyen/integrate-firebase-template>`_ that can help to add custom JavaScript & CSS to your project.

Step 1: Create a custom JavaScript file 
----------------------------------

In your theme, you can create a JavaScript file named `custom-firebase.js`, you can the name if you want. 

.. code-block:: JavaScript

    // js/custom-firebase.js

    console.log(`Custom firebase...`)
    const waitForFirebase = setInterval(() => {
        if (typeof firebase !== 'undefined' && firebase.apps.length) {
            console.log(firebase)
            firebase.auth().onAuthStateChanged(user => {
                if (user) {
                    // User logged in already or has just logged in.
                    console.log(user)
                }
            })
            clearInterval(waitForFirebase)
        }
    }, 1000)
    

This is an example function that listens to firebase authentication event. If user is logged in, you can get the user information / session. 

Your custom-firebase.js will be under js/ folder

.. figure:: /images/firestore/custom-firebase-structure.png
    :scale: 70%
    :align: center

    Custom Firebase Location

Step 2: Register your custom script
----------------------------------

After that, you need to add the script to your site. The script will be added inside the body tag for better performance.

.. code-block:: php 

    // functions.php

    // Custom JavaScript for Firebase
    function custom_firebase_scripts_function() {
        wp_enqueue_script('custom_firebase', get_template_directory_uri() . '/js/custom-firebase.js', array('firebase'), false, true);
    }

    add_action('wp_enqueue_scripts', 'custom_firebase_scripts_function');


Verify it on the front-end. You have access to firebase now.

.. figure:: /images/firestore/verity-custom-firebase.png
    :scale: 70%
    :align: center

    Verify custom firebase on frontend