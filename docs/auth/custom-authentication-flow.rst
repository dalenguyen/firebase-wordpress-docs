Custom Authentication Flow 
=============

## Custom email templates - `* Added in PRO v3.26.0`
----------------------------------

The Firebase Authentication comes with default email template for Email Verification, Forgot Password... And they are not "branded" to your business identity. 

In order to create your own email templates, you can use third party services to manage emails. This will require development skill, so you make sure that your developer know how to work with Firebase cloud functions and WordPress (PHP).

The flag `skip_default_email` and some global functions are added in order to support this feature. E.g. 

.. code-block:: php

    - send_email_confirmation (Optional) - make sure that email is verified before signing in to the website
    - skip_default_email (Optional) - skip email handling, and you must implement the email handling yourself 
    - forgot_password_link (Optional) - this will not show the forgot password form, it will lead to the forgot password page that you create 
    - forgot_password_landing_page (Optional) - after user changes password, this will redirect to page that you decide

    [firebase_auth 
        redirect="/" 
        send_email_confirmation="true" 
        skip_default_email="true" 
        forgot_password_link="/forgot-my-password"
        forgot_password_landing_page="/login"
    ]

The `skip_default_email` will not send default email template from Firebase, and you must apply your custom solution otherwise users will not receive anything. So, make you that you test it throughout before use it on production.

The next step is that you need implement those global functions in order to trigger the backend to send emails.

.. code-block:: php

    // trigger when default email is disabled for registration flow
    window.skipRegistrationDefaultEmailCallback: (user: FirebaseUser) => {}

    // trigger when default email is disabled for forgot password flow
    window.skipForgotPasswordDefaultEmailCallback: (email: string) => {}

    // trigger when default email is disabled for login flow
    window.skipLoginDefaultEmailCallback: (user: FirebaseUser) => {}


## Custom email verification process - `* Added in PRO v3.41.0`
----------------------------------

The Firebase Authentication comes with a default email verification process, and it is not customizable. However, with the PRO v3.41.0 update, you can now implement a custom email verification process.

To achieve this, you need to enable email verification and add a custom verification email page to your website.

Here are the steps to implement a custom email verification process:

    .. code-block:: php

         [firebase_auth 
              send_email_confirmation="true"
              email_verify_landing_page="/verify-email"
         ]

After user registers to your website, they will receive an email with a verification link, and they will be redirected to the email verification page that you create.

The next step is to implement the custom verification endpoint in your backend. You can retrieve user email from local storage: 

    .. code-block:: javascript

        localStorage.getItem('FIREBASE_USER_EMAIL')


From this custom page that you created, you can trigger the custom verification endpoint in your backend by sending the request with user email. For example with ajax request:

    .. code-block:: javascript

        $.ajax({
            url: 'https://your-cloud-functions.com/verify-email',
            type: 'POST',
            data: {
                email: localStorage.getItem('FIREBASE_USER_EMAIL')
            },
            success: function(response) {
                console.log(response)
            }
        })

By following these steps, you can create a custom email verification process that aligns with your business identity and requirements.

References:
- `Custom email handler <https://firebase.google.com/docs/auth/custom-email-handler>`_
- `Send custom email templates <https://blog.logrocket.com/send-custom-email-templates-firebase-react-express/>`_
- `Firebase authentication email customization <https://stackoverflow.com/a/50077575>`_