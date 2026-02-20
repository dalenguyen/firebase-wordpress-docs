.. raw:: html

    <style> .red {color:red} </style>

JWT - Restful API
=============


REST APIs JWT Authentication
----------------------------------

This feature allows you to send request to WordPress website using Firebase Id Token.

Video Guide: https://www.youtube.com/watch?v=Kq9JZq1SiYU

Remote Authentication (via URL)
----------------------------------

Imagine that you have a Firebase App that users can log in to. However, before they can use your app, users need to purchase a package that will give them permission. And this product will help to auto-login users from your Firebase App to your WooCommerce / WordPress website. This add-on doesn't care if users exist in WP or not, it just log users in with Firbase credentials. That's it.

If you want to give it a try, please visit: https://dn-wp-autologin.web.app/

Any questions or discussions, please create a ticket at https://github.com/dalenguyen/firebase-wordpress-plugin/discussions

Prerequisite
----------------------------------

- Integrate Firebase PRO users
- Firestore service is enabled
- Node 22 for deploying cloud functions

Getting Started
----------------------------------

Make sure that you have Firestore Database ready. Then apply this security rules for your collection.

.. code-block:: bash

    match /jwtTokens/{token} {
        allow read, write: if false;
    }

Then install the add-on as usual. The plugin should appear under Firebase tab.

Deploy cloud functions
----------------------------------

The cloud functions is inside the plugin, so you need to extract the zip file in order to deploy it.

Make sure that you are running Node v12. If you don't have Node on your machine, please visit `Node Version Manager <https://github.com/nvm-sh/nvm>`_.

.. code-block:: bash

    cd functions

    // install the package - you can run yarn or npm (pick one only)
    npm install

    // deploy functions
    firebase deploy --only functions --project your-project-id


You will be promted to enter the environment variables such as dashboard token, frontend token, regions. They're the same one from Integrate Firebase PRO plugin.

Create Auto-login page (WordPress)
----------------------------------

Create a WordPress page with the follow shortcode.

.. code-block:: bash

    // you can specify the redirect page after the auto-login process
    // default is home page
    // redirect is optional

    [firebase_autologin redirect="redirect-link"]


Create Redirect Page (Firebase App)
----------------------------------

This example uses JavaScript. However you can implement it by using the same principal on iOS or Android or Webapp. The key is call the callable functions for logged in users.

.. code-block:: bash

    <button id="auto-login" onclick="wpAutoLogin()">
    ...

    <script>

    // This is the WP page that you created with the shortcode
    // ?jwt= is mandatory
    const wpLink = 'https://example.com?jwt='

    const generateToken = () => {
        // Get the token from firebase
        // In case you want to trigger functions for different region
        // you can try this
        //
        // const functions = firebase.app().functions('europe-west2')
        // const token = functions.httpsCallable('users-getCustomToken')
        //

        const token = firebase.functions().httpsCallable('users-getCustomToken')
        token().then((result) => {
            if (result.data.status) {
                // if you want to redirect user after signing, please add `redirect` param to the url
                // the final url looks like: 'https://example.com?jwt=...&redirect=...'
                // so in case you want redirect user dynamicly after signing in, use the `redirect` and build your own URL.
                const url = wpLink + result.data.data.token

                // Open auto-login link for WP
                // You can also send the URL to user if you want to
                // The time limit for the link is 1 HOUR
                window.open(url, '_blank')
            } else {
                console.error(result.data.message)
            }
        })
    }

    // Start auto login process
    const wpAutoLogin = function () {
        firebase.auth().onAuthStateChanged((user) => {
            if (user) {
                generateToken()
            } else {
                console.log(`User is not logged in...`)
            }
        })
    }
    </script>

Troubleshooting
----------------------------------

IAM Service Account Credentials API
```````````````````

`IAM Service Account Credentials API has not been used in project ... before or it is disabled. Enable it by visiting...`

If you encounter this error, just click on the link and enable IAM service.

.. figure:: /images/extensions/jwt/enable-IAM-service.png
    :scale: 70%
    :align: center

    Enable IAM service


The caller does not have permission
```````````````````

`The caller does not have permission; Please refer to https://firebase.google.com/docs/auth/admin/create-custom-tokens for more details on how to use and troubleshoot this feature.`

For this error, you need to you Google Cloud Console and add `Service Account Token Creator` role to your firebase service account.

.. figure:: /images/extensions/jwt/add-service-account-token-creator.png
    :scale: 70%
    :align: center

    Enable IAM service

Migration to 2nd Gen Cloud Functions
```````````````````

This is a known issue when migrating to 2nd gen Cloud Functions. In 1st gen, the App Engine default service account had signBlob permission automatically. In 2nd gen (Cloud Run), it uses the Compute Engine default service account which lacks this permission.

The fix is to grant the Service Account Token Creator role. Run this in your terminal (requires gcloud):

.. code-block:: bash

    # Get your project number first
    gcloud projects describe YOUR_PROJECT_ID --format="value(projectNumber)"

    # Then grant the role (replace {PROJECT_NUMBER} with the number from above)
    gcloud projects add-iam-policy-binding YOUR_PROJECT_ID \
        --member="serviceAccount:{PROJECT_NUMBER}-compute@developer.gserviceaccount.com" \
        --role="roles/iam.serviceAccountTokenCreator"

Alternatively, do it in the Google Cloud Console:

1. Go to IAM & Admin → IAM
2. Find ``{PROJECT_NUMBER}-compute@developer.gserviceaccount.com``
3. Edit → Add role → Service Account Token Creator
4. Save

This grants the Compute Engine default service account (used by 2nd gen functions) the permission to call signBlob, which is required by ``auth().createCustomToken()``.
