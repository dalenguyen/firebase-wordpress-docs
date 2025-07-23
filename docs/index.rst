Complete Guide to Firebase & Supabase WordPress Integration
==========================================================

.. meta::
   :description lang=en: Guide on how to integrate Firebase & Supabase to WordPress.

Last updated: July 23, 2025


Follow `Twitter <https://twitter.com/TechCater>`_  for updates.
`Firebase & Supabase WordPress Integration <https://techcater.com/>`_ is a WordPress plugin that brings Firebase & Supabase features to WordPress site. E.g. sign in to WordPress and Firebase with one tap / email link or read & write to Firebase from WordPress.


Demo site: https://wordpress.dalenguyen.me 

Download plugin: https://techcater.com

Video Tutorials: `Youtube Playlist - Firebase WordPress Integration <https://www.youtube.com/playlist?list=PLchk3ZdnnL-bngknCj7dMQQ6JmAfSdxd8>`_

If you are interested in the development progress, please check the `Road map <https://firebase-wordpress-docs.readthedocs.io/en/latest/roadmap.html>`_.

Products
-----------

- `Integrate Firebase PRO <https://techcater.com/>`_ - `v3.41.0`
- `Firebase WordPress Functions <https://firebase-wordpress-docs.readthedocs.io/en/latest/intro/cloud-functions-deployment.html>`_ - `v2.0.0` (bundle with PRO plugin)
- `Integrate Firebase Woocommerce <https://firebase-wordpress-docs.readthedocs.io/en/latest/extensions/woocommerce.html>`_ - `v2.16.0` (Extension)
- `Integrate Firebase Users <https://firebase-wordpress-docs.readthedocs.io/en/latest/extensions/firebase-users.html>`_ - `v1.3.2` (Extension)
- `Firebase JWT <https://firebase-wordpress-docs.readthedocs.io/en/latest/extensions/jwt.html>`_ - `v1.2.1` (Extension)
- `Integrate Firebase Template <https://firebase-wordpress-docs.readthedocs.io/en/latest/extensions/firebase-template.html>`_ - `v1.1.0` (Extension)

First steps
-----------

This guide is mostly for the PRO version, if you are using the FREE version, please refer to the `WordPress.org Guide <https://wordpress.org/plugins/integrate-firebase/>`_

* :doc:`/intro/introduction`
* :doc:`/intro/ifp-plugin-configuration`
* :doc:`/intro/cloud-functions-deployment`
* :doc:`/intro/shortcode-list`
* :doc:`/intro/update-plugin`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: First steps

   /intro/introduction
   /intro/ifp-plugin-configuration
   /intro/cloud-functions-deployment
   /intro/shortcode-list
   /intro/update-plugin

Authentication
-----------

Even though the plugin allows Firebase users to log in to WordPress at the same time, best scenario is to use WordPress as backend for Firebase without allowing users to login to WordPress.

* :doc:`/auth/new-social-login`
* :doc:`/auth/work-with-firebaseui-web`
* :doc:`/auth/register-login-form`
* :doc:`/auth/custom-registration-form`
* :doc:`/auth/onetap-email-signin`
* :doc:`/auth/wordpress-user-integration`
* :doc:`/auth/firebase-user-profile`
* :doc:`/auth/firebase-users-managment`
* :doc:`/auth/2fa`
* :doc:`/auth/custom-authentication-flow`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Authentication

   /auth/new-social-login
   /auth/work-with-firebaseui-web
   /auth/register-login-form
   /auth/custom-registration-form
   /auth/onetap-email-signin
   /auth/wordpress-user-integration
   /auth/firebase-user-profile
   /auth/firebase-users-managment
   /auth/2fa
   /auth/custom-authentication-flow

Database
-----------

From WordPress, users can retrieve or write data from Firebase Realtime / Firestore using shortcodes.

* :doc:`/database/retrieve-data-from-firestore`
* :doc:`/database/display-firestore-with-pagination`
* :doc:`/database/dynamically-display-from-firestore`
* :doc:`/database/save-data-realtime-firestore`
* :doc:`/database/work-with-firebase-custom-claims`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Database

   /database/retrieve-data-from-firestore
   /database/display-firestore-with-pagination
   /database/dynamically-display-from-firestore
   /database/save-data-realtime-firestore
   /database/work-with-firebase-custom-claims

Cloud Storage
-----------

Cloud Storage is built for app developers who need to store and serve user-generated content, such as photos or videos.

* :doc:`/storage/cloud-storage-integration`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Cloud Storage

   /storage/cloud-storage-integration

Analytics
-----------

At the heart of Firebase is Google Analytics, a free and unlimited analytics solution.

* :doc:`/analytics/configure-analytics`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Analytics

   /analytics/configure-analytics

Firebase Features
-----------

* :doc:`/firebase/post-to-firebase`
* :doc:`/firebase/users-to-firebase`
* :doc:`/firebase/firebase-cloud-message`
* :doc:`/firebase/firebase-app-check`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Firebase Features

   /firebase/post-to-firebase
   /firebase/users-to-firebase
   /firebase/firebase-cloud-message
   /firebase/firebase-app-check

Hooks
-----------

Actions & Filters that help to communicate with Firebase.

* :doc:`/hooks/pro-filters`
* :doc:`/hooks/pro-actions`
* :doc:`/hooks/woo-filters`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Hooks

   /hooks/pro-filters
   /hooks/pro-actions
   /hooks/woo-filters

Developers
-----------

If you are a developer, there is no limit that you cannot extend the plugin bases on you needs. Here are some examples.

* :doc:`/developer/add-custom-scripts`
* :doc:`/developer/retrieve-data`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Developers

   developer/add-custom-scripts
   developer/retrieve-data

Extensions
-----------

List of plugins that can integrate with **Integrate Firebase PRO**

* :doc:`/extensions/firebase-template`
* :doc:`/extensions/firebase-users`
* :doc:`/extensions/woocommerce`
* :doc:`/extensions/jwt`
* :doc:`/extensions/google-maps`
* :doc:`/extensions/buddypress`
* :doc:`/extensions/video-chat`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Extensions

   extensions/firebase-template
   extensions/firebase-users
   extensions/woocommerce
   extensions/jwt
   extensions/google-maps
   extensions/buddypress
   extensions/video-chat

Experiments
-----------

Experiments for future features

* :doc:`/experiments/update-profile`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Usecases

   /experiments/update-profile

Usecases
-----------

Use Cases for Integrate Firebase PRO

* :doc:`/usecases/wordpress-cms`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Usecases

   /usecases/wordpress-cms

Miscellaneous
-----------

* :doc:`/misc/plugin-incompatibility`
* :doc:`/misc/troubleshooting`
* :doc:`/misc/performance`
* :doc:`/misc/internationalization`
* :doc:`/misc/roadmap`
* :doc:`/misc/changelog`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Miscellaneous

   /misc/troubleshooting
   /misc/performance
   /misc/internationalization
   /misc/roadmap
   /misc/changelog

.. .. toctree::
..    :maxdepth: 2
..    :caption: Contents:

..    introduction
..    firebase-wordpress-integration
..    shortcode-list
..    work-with-firebaseui-web
..    firebase-users-managment
..    firebase-user-profile
..    wordpress-user-integration
..    wordpress-to-firebase
..    firebase-cloud-message
..    save-data-realtime-firestore
..    retrieve-data-from-firestore
..    work-with-firebase-custom-claims
..    internationalization
..    usecases
..    extensions-google-maps
..    extensions-buddypress
..    performance
..    troubleshooting
..    roadmap
..    change-log
