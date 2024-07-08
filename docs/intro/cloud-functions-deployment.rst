Firebase Cloud Functions Deployment
=============

If you are using PRO version, there is another folder named **firebase-wordpress-functions**. If you want to manage database, Firebase users and custom functions, you should deploy the functions together with the plugin. Make sure that you have Nodejs installed on your machine. 

The cloud functions is only Admin Dashboard tasks, you don't have to deploy the cloud functions for frontend interactions such as login, display or retrieve data.

If you want a hands-on guide, you can watch this tutorial: `How to Deploy Cloud Functions <https://www.youtube.com/watch?v=D-xvzJ9K8jw>`_

.. raw:: html

    <div style="position: relative; padding-bottom: 10%; height: 0; overflow: hidden; max-width: 100%; height: auto;">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/D-xvzJ9K8jw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>

Prerequisite
`````````````

In order to deploy cloud functions, you need to have `Nodejs v18 <https://nodejs.org/dist/latest-v18.x/>`_ installed on your machine. 

On Google Cloud Platform, go to your project and make sure Cloud Build API and Cloud Functions are enabled. And the account that you use to deploy has `Service Account User` and `Cloud Functions Admin` Role in order to deploy cloud functions to Firebase.

Then install `firebase-tools <https://firebase.google.com/docs/cli>`_ packaged

.. code-block:: bash

    npm install -g firebase-tools

SignIn and test firebase cli

.. code-block:: bash

    firebase login

Since version 0.6.0, before deploying any functions, you should create two tokens for security purpose. One for Wordpress dashboard usage, the other is for WordPress frontend.

.. code-block:: bash

    // Generate two random tokens - save in notepad, you will need them later

    // DASHBOARD_TOKEN
    node -e "console.log(require('crypto').randomBytes(20).toString('hex'))"

    // FRONTEND_TOKEN
    node -e "console.log(require('crypto').randomBytes(20).toString('hex'))"

Change Your Plan to Blaze
`````````````

**Why will I need a billing account to use the Node.js 10 runtime for Cloud Functions for Firebase?**

Because of updates to its underlying architecture planned for August 17, 2020, Cloud Functions for Firebase will rely on some additional paid Google services: Cloud Build, Container Registry, and Cloud Storage. These architecture updates will apply for functions deployed to the Node.js 10 runtime. `Usage of these services will be billed in addition to existing pricing <https://firebase.google.com/support/faq#pricing-blaze-free>`_.

.. figure:: /images/intro/pay-as-you-go.png
    :scale: 70%
    :align: center

    Firebase pricing plans

Change Cloud Functions Regions
`````````````

You can type the name of the region that you want to deploy the cloud functions at deploy time. 

.. code-block:: bash

    ? Enter a string value for FRONTEND_TOKEN: YOUR_SECRET_TOKEN
    ? Enter a string value for DASHBOARD_TOKEN: YOUR_SECRET_TOKEN
    ? Enter a string value for REGIONS: us-central1
    ? Enter an integer value for USER_API_MININSTANCES: 0

After configuration, those information will be saved to an environment file in your folder:

.. code-block:: bash

    i  functions: Created new local file .env.YOUR_PROJECT_ID to store param values. We suggest explicitly adding or excluding this file from version control.


If you want to change the region of the cloud function, you can update the file and redeploy the cloud functions.

Install Packages & Deploy Cloud Functions
`````````````

Install packages and build functions. I'm using Yarn, you can use npm if you want.

.. code-block:: bash

    cd functions/
    yarn OR npm install

The code will go to *functions* folder, then installs packages with yarn / npm.

Start deploying firebase functions

.. code-block:: bash

    cd functions
    firebase deploy --only functions --project project-id

The deployment result should look like this

.. code-block:: bash 

    ✔  functions: Finished running predeploy script.
    i  functions: ensuring necessary APIs are enabled...
    ✔  functions: all necessary APIs are enabled
    i  functions: preparing functions directory for uploading...
    i  functions: packaged functions (103.29 KB) for uploading
    ✔  functions: functions folder uploaded successfully
    i  functions: updating Node.js 10 (Beta) function api-user(us-central1)...
    i  functions: updating Node.js 10 (Beta) function api-database(us-central1)...
    ✔  functions[api-user(us-central1)]: Successful update operation. 
    ✔  functions[api-database(us-central1)]: Successful update operation. 

    ✔  Deploy complete!

    Project Console: https://console.firebase.google.com/project/project-id/overview
    ✨  Done in 77.56s.

After that, you should update your Firebase setting with the dashboard token and frontend token and firebase functions url (e.g. *https://us-central1-project-id.cloudfunctions.net*)

.. figure:: /images/firebase-setting.png
    :scale: 70%
    :align: center

    Firebase setting

Just to verify that everything works, you can find three cloud functions in your firebase console after the deployment. 

.. figure:: /images/firebase-cloud-functions.png
    :scale: 70%
    :align: center

    Firebase cloud functions