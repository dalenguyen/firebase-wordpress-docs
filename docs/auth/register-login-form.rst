Register & Login Form
=============

If you don't want to use FirebaseUI Web, you can create a custom login or registration form in order to authenticate with Firebase & WordPress.

Demo: https://wordpress.dalenguyen.me/register-login-form/

Login Form
----------------------------------

This form only support log in though email, and you can style it freely. If you want to hide the label and display placeholder to display email password, you can add a flag name `enable_placeholder` to the shortcode 

.. code-block:: php

    // After logging in, you will be redirect to the homepage. 
    //
    // `redirect` is optional. 
    // `button_text` is optional. Default button text is "Login"
    // `enable_placeholder` is optional 

    [firebase_login button_text='Signin' redirect='/' enable_placeholder=true]

Registration Form
----------------------------------

With this form, you can customize the registration form that will save extra fields such as phone number.

.. code-block:: php

    // Registration will extra fields: first name, last name phone number. 
    // The redirect, extra fields and requried fields are optional. 
    // Without those, it will only show email and password fields.

    [firebase_register required_fields='firstName,lastName,phoneNumber' extra_fields='firstName,lastName,phoneNumber' redirect='/']

    If you want to send a verification email after user registers, you can add this option: send_email_confirmation=true
    Remember that if user doesn't verify their email, they won't be allowed to login next time.

    If you want to send user to a custom page after they register, you can add this option: email_verify_landing_page='/verify-email'. This option must be used with send_email_confirmation=true.

Logout Option
----------------------------------

This shortcode will show a Logout button after a user signs in.

.. code-block:: php

    // Logout Button
    // redirect after logging out and button_text are optional

    [firebase_logout redirect="/" button_text="Sign Out"][/firebase_logout]