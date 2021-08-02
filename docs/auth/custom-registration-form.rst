Custom Registration Form (Contact 7)
=============

This feature is added since v2.15.1. The purpose of the feature is to provide a custom registration form for the user. 

Instead of having email & password only, now you can have extra fields like name, address, phone number, etc.


Demo: https://wordpress.dalenguyen.me/custom-registration-c7-form/
Video: https://youtu.be/IzfS0Hok6mg

Contact 7 Form Creation 
----------------------------------

Here is a simple example of how to use the custom registration form. 

These hidden fields are optional.

.. code-block:: php

    [hidden sendEmailConfirmation1 "true"]
    [hidden redirect "/my-account"]

    <label> First Name
        [text* firstName]
    </label>

    <label> Last Name
        [text* lastName]
    </label>

    <label> Gender
        [select gender "Male" "Female" "Other"]
    </label>

    <label> Email
        [email* email] </label>

    <label> Password
        [password* password password_min:6]
    </label>

    <label> Password Confirmation
        [password* password_validate password_check:password]
    </label>

    [submit "Register"]


Embed Registration Form in a Page
----------------------------------

After you have created the form, you can embed it in a page. Remember to put **html_id="if-c7-registration-form"** in the form tag. 

.. code-block:: php

    [contact-form-7 id="211" title="Registration" html_id="if-c7-registration-form"]


If you want to save extra fields to firebase, please check `Sync User Data From WordPress to Firebase
<https://firebase-wordpress-docs.readthedocs.io/en/latest/firebase/users-to-firebase.html>`_