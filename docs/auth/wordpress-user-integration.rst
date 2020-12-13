.. raw:: html

    <style> .red {color:red} </style>

WordPress User Integration
=============

This feature solves the authentication problem. This is an example from one of my potential clients. The client has a mobile app (Firebase users), and they want those users to login to a separate WordPress website without registering again. 

And this plugin can help you to achieve just that. Authentication also work for WordPress multisite.

At this stage, it helps to authenticate to WordPress dashboard with a **subscriber** or **customer** role (WooCommerce). And the password will be dominated by Firebase Users. User cannot change password when logging into WordPress dashboard. They have to use *forgot password* feature in Firebase in order to create a new password. And if the password is different in both systems, the next time user logs in through FirebaseUI Web shortcode, it will change the password in WordPress automatically.

**Support**: Social Logins, Email and Phone Number.

Firebase UID will be used as WordPress username. If they have display name from Firebase (e.g. Google login), it will update WordPress display name for a friendly user experience.

.. figure:: /images/auth/user-display-name.png
    :scale: 70%
    :align: center

    User Display Name in WooCommerce

Login to WP Dashboard with Firebase Users
----------------------------------

.. role:: red

**Important:** :red:`Before doing this, you should keep a dashboard open for yourself, and open another private window in order to login with an email from Firebase, then assign the Admin right to that user before you log out of current window - to make sure that you can log in again with your Firebase user (with **admin** rights)`. 

In case of logging out without assign another user with admin rights, you can rename the plugin folder, and login as usual.

This flow will utilize FirebaseUI Web workflow in order to authenticate users. In order to that, you have to log in to WordPress Dashboard, then **Dashboard > Firebase > Auth**.

.. figure:: /images/auth/wp-login-with-firebase.png
    :scale: 70%
    :align: center

    Firebase Auth Settings

Check **Allow Login to WP Dashboard** and enter you **Login Url**. It could be your homepage or a separate page just for logging in. From now, everytime users navigate to https://your-webiste.com/wp-admin, it will redirect to your new login page.

This page will contain the shortcode for logging in.

.. code-block:: php

    // Login, Register through FirebaseUI Web
    [firebaseui_web redirect='link-to-page'][/firebaseui_web]

.. figure:: /images/auth/wp-new-login-url.png
    :scale: 70%
    :align: center

    New WP Login Page

After users log in, it will create a new user in WordPress if the user doesn't exist. Then authenticate it to WordPress dashboard automatically. In `PRO - v1.17.0`, while user logging in, there will be a loading state that prevents users from navigating to other pages until the login process is completed.

One thing to notice that, after user logs in via the plugin shortcode, the firebase uid is saved in user metadata, and you can retrive it by using this example. 

.. code-block:: php

    // This will return an array with firebase uid
    $firebase_uid = get_user_meta( $user->ID , 'firebase_uid', true );
    error_log($firebase_uid);

**Notice**: :red:`the WordPress username defaults to Firebase UID, and their display name will be set as Firebase Display Name or Phone Number (via phone authentication). User can change their display name if they want. This is only affect since v1.4.0`

When users log out from dashboard, that means they will also be logged out to Firebase.

Create a new WordPress User through API
----------------------------------

The Integrate Firebase PRO has its own Restful API endpoints that help to create a new WordPress user.
In this scenario, when you have a mobile app, and you want to duplicate user in WordPress, you can call the API to create a new User after user register on your app.

.. code-block:: php

    Endpoint: POST https://example.com/firebase/v2/users/register

    Example payload: {
        username: 'dale',
        email: 'dale@dalenguyen.me',
        password: 'the-password'
    }