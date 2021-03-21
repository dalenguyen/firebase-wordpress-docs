.. raw:: html

    <style> .red {color:red} </style>

Enable FirebaseUI Web
=============

.. role:: red

This feature will help to you register, login and logout on WordPress with your Firebase Users. :red:`However, this won't let your users login to WordPress Dashboard. If you want to sync the Users between two systems, please read the WordPress User Integration section in this guide`.

Go to `WordPress User Integration Section <https://firebase-wordpress-docs.readthedocs.io/en/latest/auth/wordpress-user-integration.html>`_.

Before showing the `FirebaseUI Web <https://github.com/firebase/firebaseui-web>`_ on your WordPress, you need to enable sign-in options in *Firebase > Authentication*

.. figure:: /images/auth/enable-sign-in-options.png
    :scale: 70%
    :align: center

    Enable SignIn Options

Since version 0.5.5, all the authentication methods will be handled through FirebaseUI-Web. 

.. code-block:: bash

    // Deprecated shortcodes
    [firebase_user_register] and [firebase_login]

You need to update the Auth settings in Firebase, in order to enable this feature.

.. figure:: /images/auth/firebaseui-web-settings.png
    :scale: 70%
    :align: center

    FirebaseUI Web Settings

Then you well the login feature on the frontend.

.. figure:: /images/auth/firebaseui-web-frontend.png
    :scale: 70%
    :align: center

    FirebaseUI Web Frontend

You can enable the login feature by adding this shorcode a post or a page. If you specify the `redirect` parameter in the shortcode, it will override the setting in WordPress in order to redirect to desired page after logging in.

.. code-block:: php

    // redirect & send_email_confirmation are optional
    [firebaseui_web redirect="link-to-page" send_email_confirmation=true][/firebaseui_web]