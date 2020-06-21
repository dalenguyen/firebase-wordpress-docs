Complete Guide to Firebase WordPress Integration (v1.3.0)
==========================================================

.. meta::
   :description lang=en: Guide on how to integrate Firebase to WordPress.

Last updated: June 21, 2020

`Integrate Firebase PRO <https://firebase.dalenguyen.me/>`_ is a WordPress plugin that brings Firebase features to WordPress site. E.g. sign in to WordPress and Firebase with one tap / email link or read & write to Firbase from WordPress.

Demo site: https://wordpress.dalenguyen.me 

Video Tutorials: `Youtube Playlist - Firebase WordPress Integration <https://www.youtube.com/playlist?list=PLchk3ZdnnL-bngknCj7dMQQ6JmAfSdxd8>`_

If you are interested in the development progress, please check the `Road map <https://firebase-wordpress-docs.readthedocs.io/en/latest/roadmap.html>`_.

First steps
-----------

This guide is mostly for the PRO version, if you are using the FREE version, please refer to the `WordPress.org Guide <https://wordpress.org/plugins/integrate-firebase/>`_

* :doc:`/intro/introduction`
* :doc:`/intro/ifp-plugin-configuration`
* :doc:`/intro/cloud-functions-deployment`
* :doc:`/intro/shortcode-list`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: First steps

   /intro/introduction
   /intro/ifp-plugin-configuration
   /intro/cloud-functions-deployment
   /intro/shortcode-list

Authentication
-----------

Even though the plugin allows Firebase users to log in to WordPress at the same time, best scenario is to use WordPress as backend for Firebase without allowing users to login to WordPress.

* :doc:`/auth/work-with-firebaseui-web`
* :doc:`/auth/onetap-email-signin`
* :doc:`/auth/wordpress-user-integration`
* :doc:`/auth/firebase-user-profile`
* :doc:`/auth/firebase-users-managment`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Authentication

   /auth/work-with-firebaseui-web
   /auth/onetap-email-signin
   /auth/wordpress-user-integration
   /auth/firebase-user-profile
   /auth/firebase-users-managment

Database
-----------

From WordPress, users can retrive or write data from Firbase Realtime / Firestore using shortcodes.

* :doc:`/database/retrieve-data-from-firestore`
* :doc:`/database/save-data-realtime-firestore`
* :doc:`/database/work-with-firebase-custom-claims`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Database

   /database/retrieve-data-from-firestore
   /database/save-data-realtime-firestore
   /database/work-with-firebase-custom-claims

Firebase Features
-----------

* :doc:`/firebase/wordpress-to-firebase`
* :doc:`/firebase/firebase-cloud-message`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Firebase Features

   /firebase/wordpress-to-firebase
   /firebase/firebase-cloud-message

Extentions
-----------

List of plugins that can integrate with **Integrate Firebase PRO**

* :doc:`/extentions/google-maps`
* :doc:`/extentions/buddypress`
* :doc:`/extentions/woocommerce`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Extentions

   extentions/google-maps
   extentions/buddypress
   extentions/woocommerce

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
