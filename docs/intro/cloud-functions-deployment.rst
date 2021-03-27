Firebase Cloud Functions Deployment
=============

If you are using PRO version, there is another folder named **firebase-wordpress-functions**. If you want to manage database, Firebase users and custom functions, you should deploy the functions together with the plugin. Make sure that you have Nodejs installed on your machine. 

The cloud functions is only Admin Dashboard tasks, you don't have to deploy the cloud functions for frontend interactions such as login, display or retrieve data.

If you want a hands-on guide, you can watch this tutorial: `How to Deploy Cloud Functions <https://www.youtube.com/watch?v=D-xvzJ9K8jw>`_

.. raw:: html

    <div style="position: relative; padding-bottom: 10%; height: 0; overflow: hidden; max-width: 100%; height: auto;">
        <iframe width="560" height="315" src="https://www.youtube.com/watch?v=D-xvzJ9K8jw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>

Prerequisite
`````````````

In order to deploy cloud functions, you need to have `Nodejs v12 <https://nodejs.org/dist/latest-v12.x/>`_ installed on your machine. 

On Google Cloud Platform, go to your project and make sure Cloud Buid API and Cloud Functions are enabled. And the account that you use to deploy has `Service Account User` Role in order to deploy cloud functions to Firebase.

Then install `firebase-tools <https://firebase.google.com/docs/cli>`_ packaged

.. code-block:: bash

    npm install -g firebase-tools

SignIn and test firebase cli

.. code-block:: bash

    firebase login

Since version 0.6.0, before deploying any functions, you should create two tokens for security purpose. One for Wordpress dashboard usage, the other is for Wordress frontend.

.. code-block:: bash

    // Generate random token
    node -e "console.log(require('crypto').randomBytes(20).toString('hex'))"

    // Set your token to firebase configuration (dashboard token)
    firebase functions:config:set api.dashboard_token=your-secret-key --project project-id

    // Set your token to firebase configuration (frontend token)
    firebase functions:config:set api.frontend_token=your-secret-key --project project-id

    // Check your api token
    firebase functions:config:get api --project project-id

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

Default functions will be deployed to `us-central1`. If you don't want to change the regions, please skip this part.

In case you want to change the deploy regions to `asia-east2`, you can set a regions configuration for the firebase.

.. code-block:: bash

    // Set deploy regions for `asia-east2`
    firebase functions:config:set regions.0=asia-east2 --project project-id

    // Set deploy regions for `asia-east2` and `us-central1`
    firebase functions:config:set regions.0=asia-east2 regions.1=us-central1 --project project-id

After configuration, please check your environment to make sure that you have the region in the functions config.

.. code-block:: bash

    firebase functions:config:get regions --project project-id

    // The result should looks like this for two regions (asia-east2 & us-central1)
    [
        "asia-east2",
        "us-central1"
    ]

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
    yarn deploy --project project-id
    // OR 
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

After that, you should update your Firebase setting with the dashboad token and frontend token and firebase functions url (e.g. *https://us-central1-project-id.cloudfunctions.net*)

.. figure:: /images/firebase-setting.png
    :scale: 70%
    :align: center

    Firebase setting

Just to verify that everything works, you can find three cloud functions in your firebase console after the deployment. 

.. figure:: /images/firebase-cloud-functions.png
    :scale: 70%
    :align: center

    Firebase cloud functions