.. raw:: html

    <style> .red {color:red} .green {color: green} </style>

Integrate Firebase Users
=============

.. role:: red

:red:`This is not a standalone product. In order to use this extension, you need to install at least Integrate Firebase PRO (v1.21.0) and Firebase WordPress functions (v0.15.0).`

The sole purpose of this plugin is to help web masters to migrate WordPress users to Firebase. **This should be done one in production to avoid users duplication!**

Install the extension
----------------------------------

After downloading the extension, you can install and active the plugin. You will find it under **Firebase > Import Users**.

.. figure:: /images/extensions/firebase-users/active-firebase-users.png
    :scale: 70%
    :align: center

    Active Firebase Users plugin 

As you can see, there is 159 users in WordPress

Import WordPress Users to Firebase
----------------------------------

In order to import WordPress users to Firebase, you just need to press the button **Import WP Users to Firebase**, and the plugin will do its magic.

.. role:: note

:green:`If you have more than 10,000 users, please try to increase max_execution_time & memory_limit in PHP. If it still doesn't work, please contact me for further support.`


The Firebase UID will be the WordPress **user_login**. It's because if uid is generated randomly, it will create another user with the same email. You can have a look the `Firebase Docs <https://firebase.google.com/docs/auth/admin/import-users#usage>`_ .

.. role:: note

:red:`Please note that if users don't have an email, it will not be imported to Firebase.`

.. figure:: /images/extensions/firebase-users/successfully-import-wordprses-users.png
    :scale: 70%
    :align: center

    Successfully imported Users from WordPress to Firebase

I recommend that you should try the plugin in your local machine or development environment before moving to production.