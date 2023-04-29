Social Login (NEW)
=============

This feature is added since v3.5.0. The purpose of this feature is to provide a all in one place authentication flow for customers. Customers will have options to login either using social media, phone (OTP) or email & password without leaving the current page. 

Demo: https://wordpress.dalenguyen.me/social-login-new/

Video: https://www.youtube.com/watch?v=j_2apwBk9Js

What you need to do is add this shortcode to any page, then you will have a complete social login. 

- redirect: redirect to a page after signing in or signing up 
- send_email_confirmation: verify email after signing up 
- skip_default_email: skip sending default email in case you want to implement your own email server
- forgot_password_link: lead users to another page if they want to reset their password 
- default_login_form: whether you want to show Sign In or Sign Up form first

.. code-block:: php

   [firebase_auth 
    redirect="/" 
    send_email_confirmation=true 
    skip_default_email=false 
    forgot_password_link="/forgot-my-password" 
    default_login_form=true]


.. figure:: /images/auth/new-social-login.png
    :scale: 70%
    :align: center

    New Social Login