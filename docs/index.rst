Complete Guide to Firebase WordPress Integration
==========================================================

.. meta::
   :description lang=en: Guide on how to integrate Firebase to WordPress.

Last updated: Jan 24, 2021

.. raw:: html

   <!-- Begin Mailchimp Signup Form -->
   <link href="//cdn-images.mailchimp.com/embedcode/slim-10_7.css" rel="stylesheet" type="text/css">
   <style type="text/css">
      #mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; }
      /* Add your own Mailchimp form style overrides in your site stylesheet or in this style block.
         We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
   </style>
   <div id="mc_embed_signup">
   <form action="https://dalenguyen.us8.list-manage.com/subscribe/post?u=a51d489a312958f77170fa75d&amp;id=9168c0bdaf" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
      <div id="mc_embed_signup_scroll" style="width: 100%">
         <label for="mce-EMAIL">SUBSCRIBE FOR UPDATES</label>
         <br>
         <input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="email address" required width="100%">
         <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
         <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_a51d489a312958f77170fa75d_9168c0bdaf" tabindex="-1" value=""></div>
         <br><br>
         <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
      </div>
   </form>
   </div>

   <!--End mc_embed_signup-->
   <br>


`Integrate Firebase PRO <https://firebase.dalenguyen.me/>`_ is a WordPress plugin that brings Firebase features to WordPress site. E.g. sign in to WordPress and Firebase with one tap / email link or read & write to Firbase from WordPress.


Demo site: https://wordpress.dalenguyen.me 

Download plugin: https://firebase.dalenguyen.me

Video Tutorials: `Youtube Playlist - Firebase WordPress Integration <https://www.youtube.com/playlist?list=PLchk3ZdnnL-bngknCj7dMQQ6JmAfSdxd8>`_

If you are interested in the development progress, please check the `Road map <https://firebase-wordpress-docs.readthedocs.io/en/latest/roadmap.html>`_.

Products
-----------

- `Integrate Firebase PRO <https://firebase.dalenguyen.me/>`_ - `v2.3.1`
- `Firebase WordPress Functions <https://firebase-wordpress-docs.readthedocs.io/en/latest/intro/cloud-functions-deployment.html>`_ - `v0.18.0` (bundle with PRO plugin)
- `Integrate Firebase Woocommerce <https://firebase-wordpress-docs.readthedocs.io/en/latest/extensions/woocommerce.html>`_ - `v1.5.0` (Extension)
- `Integrate Firebase Users <https://firebase-wordpress-docs.readthedocs.io/en/latest/extensions/firebase-users.html>`_ - `v1.0.0` (Extension)
- `Integrate Firebase Template <https://firebase-wordpress-docs.readthedocs.io/en/latest/extensions/firebase-template.html>`_ - `v1.0.0` (Extension)

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

* :doc:`/auth/work-with-firebaseui-web`
* :doc:`/auth/register-login-form`
* :doc:`/auth/onetap-email-signin`
* :doc:`/auth/wordpress-user-integration`
* :doc:`/auth/firebase-user-profile`
* :doc:`/auth/firebase-users-managment`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Authentication

   /auth/work-with-firebaseui-web
   /auth/register-login-form
   /auth/onetap-email-signin
   /auth/wordpress-user-integration
   /auth/firebase-user-profile
   /auth/firebase-users-managment

Database
-----------

From WordPress, users can retrive or write data from Firbase Realtime / Firestore using shortcodes.

* :doc:`/database/retrieve-data-from-firestore`
* :doc:`/database/dynamically-display-from-firestore`

* :doc:`/database/save-data-realtime-firestore`
* :doc:`/database/work-with-firebase-custom-claims`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Database

   /database/retrieve-data-from-firestore
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

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Firebase Features

   /firebase/post-to-firebase
   /firebase/users-to-firebase
   /firebase/firebase-cloud-message

Hooks
-----------

Actions & Filters that help to communicate with Firebase.

* :doc:`/hooks/filters`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Hooks

   /hooks/filters

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
* :doc:`/extensions/google-maps`
* :doc:`/extensions/buddypress`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Extensions

   extensions/firebase-template
   extensions/firebase-users
   extensions/woocommerce
   extensions/google-maps
   extensions/buddypress

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
