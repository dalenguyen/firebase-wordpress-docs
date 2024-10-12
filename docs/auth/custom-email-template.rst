Custom Email Template 
=============

`* Added in PRO v3.26.0`

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