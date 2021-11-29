.. raw:: html

    <style> .red {color:red} </style>

IF-PRO Plugin Configuration
=============

.. role:: red

:red:`Please deactivate and remove the Free plugin before installing the Integrate Firebase PRO version.`

Download the Integrate Firebase PRO plugin
----------------------------------

There is a FREE version of this `Firebase WordPress integration plugin <https://wordpress.org/plugins/integrate-firebase/>`_ that you can find in WordPress plugin site. You can give it a try, however, the application is very limited. If you only want to interact with Firebase through WordPress frontend only, then the free version would be sufficient enough.

So, if you want a more secured and advanced feature of the plugin, support the development of `Integrate Firebase PRO <https://techcater.com>`_ version.

Prepare Firebase Credentials
----------------------------------
Before using the plugin, we need have the credentials from Firebase Console. You can get it by logging into https://console.firebase.google.com. 

After signing in, you can navigate to **Project Overview > Project Settings**.

.. figure:: /images/firebase-project-settings.png
    :scale: 70%
    :align: center

    General configuration

In General tab, you can get the config at the bottom. If you don't have any app ready, you can create a new one. 

.. figure:: /images/firebase-create-web-app.png
    :scale: 70%
    :align: center

    Create a Web app

After creating a web app for you project, you can save your credentials for later usage.

.. figure:: /images/firebase-credentials.png
    :scale: 70%
    :align: center

    Firebase Credentials

Installation Process
----------------------------------

After you have downloaded the plugin, uncompress the zip file in order to install the plugin file (**integrate-firebase-PRO.zip**). You can use default installation process in order to install the plugin. Otherwise, you can always manually upload the plugin to your plugin folder through FTP client.

After you activate the plugin, you need to enter the Firebase credentials in the **Dashboard > Firebase**.

.. figure:: /images/general.png
    :scale: 70%
    :align: center

    General configuration

After that, you can create login form, show data, show logout button… on WordPress frontend.

Select Firebase Services - Optimization
----------------------------------

With the new update since v1.1.0 you have to pick the services (General Tab) for optimization purposes. I have choose either Realtime / Firestore or both of them in order to interact with Firebase Database on the frontend.

.. figure:: /images/general/firebase-optimization.png
    :scale: 70%
    :align: center

    Firebase Optimization