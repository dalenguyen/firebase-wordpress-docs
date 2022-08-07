.. raw:: html

    <style> .red {color:red} </style>

Save Data from WordPress to Firebase (Realtime + Firestore)
=============

**If your Contact7 is >= v.5.2, please use update this plugin to the latest version (>= v1.5.0).**

In this guide, I will show you how to add new data to Realtime database Firestore. In this example, I use `Contact Form 7 <https://wordpress.org/plugins/contact-form-7/>`_, but you feel free to design your own form or use other plugin. 

The reason that I use Contact Form 7 is because it's the most popular form in WordPress plugin. It is well supported and highly customisation. You don't have to worry about form validation or email handling after submitting a form.

If you decide to create your own custom form, remember to add "if-create-data-form" as an ID to your form, together with the hidden fields below.

.. figure:: /images/database/custom-form.png
    :scale: 70%
    :align: center

    Custom Create Form

Prerequisite
----------------------------------

Since **v0.17.0**, you only need to update security rules on your database (realtime / firestore), so any can write to your database or they have to log in before saving. It totally depends on the firebase security rules.

.. role:: red

:red:`Note: if you use 'Contact 7 Redirect' feature, it may not work properly because the redirect may interfere with the sync process.`


Getting Firebase UID value
----------------------------------

If you want to get the Firebase UID to any inputs as a value. You can add a special class `getFirebaseUid` to the input fields.

.. code-block:: html 

    // Sample contact 7 input
    [hidden documentId class:getFirebaseUid "INVALID"]

    // Sample html input 
    <input type="text" name="documentId" value="will-be-generated" class="getFirebaseUid">


Example of creating new form and writing data to Firestore
----------------------------------

Sample of data that I will use to update to Firestore

.. code-block:: bash

    export interface Contact {
        firstName: string
        lastName: string
        email: string
        phone: string
        age: string
        dateOfBirth: string
        hobbies: array<string>
        food: array<string>
        gender: string
    }

The `createdAt` field will be added automatically for sorting purpose.

From that you can create a sample form in Contact tab. The hidden fields are important. 

+ [hidden collectionName "users"]  -> collection name is users.
+ [hidden documentId "your-document-name"] -> it will override the document id 1. This field is optional.
+ [hidden databaseType "firestore"] -> data will be saved in firestore.
+ [hidden keyId "YOUR-ID-KEY-NAME"] -> data will be saved in firestore together with the document id.
+ [hidden arrayType "hobbies,food"] -> array data should be added to arrayType field. This field is optional.
+ [hidden dateType "dateOfBirth"] -> will save as ISO string type. This field is optional.
+ [hidden mapTypes "contact"] -> will save a map (object) type
+ [hidden integerTypes "age,phone"] -> will save as integer type
+ [hidden formAction "UPDATE"] -> This option is DEPRECATED.

The default option is to upsert data to firebase. If the node / id does not exist, it will create a new one; otherwise, it it update the existing data.

Subcollection is also supported. If you want to save under subcollection, you just need to update the hidden field. For example `[hidden collectionName "users/test/products"]` will save data under `products` subcollection. The plugin also supports userId as the document name. For example, `[hidden collectionName "users/getFirebaseUid/products"]` will save data under firebase uid document.



.. code-block:: bash

    [hidden collectionName "users"]
    [hidden documentId "your-document-name"]
    [hidden databaseType "firestore"]
    [hidden arrayType "hobbies,food"]
    [hidden dateType "dateOfBirth"]
    [hidden mapTypes "contact"]
    [hidden integerTypes "age"]

    [text* firstName placeholder "First Name"]
    [text* lastName placeholder "Last Name"]
    [text* email placeholder "Email"]
    [tel phone placeholder "+1 647 620 0000"]

    <label for="age">Age</label>
    [number age id:age min:1 max:100]

    <label for="dateOfBirth">Date of Birth</label>
    [date* dateOfBirth id:dateOfBirth]

    [text* contact__firstName placeholder "Contact First Name"]
    [text* contact__lastName placeholder "Contact Last Name"]

    <label for="contact__sex">Contact Sex</label>
    [select* contact__sex id:contact__sex "Male" "Female" "Other"]

    <label for="hobbies">Hobbies</label>
    [select* hobbies id:hobbies multiple "Archery" "Slap Dance" "Rock Climbing"]

    <label for="food">Food</label>
    [checkbox food id:food "Pho" "Ramen" "Dimsum"]

    <label for="gender">Gender</label>
    [radio gender id:gender default:1 "Male" "Female" "Other"]

    [submit id:if-data-submit "Submit"]

The shortcode will be added to the WordPress page or post. With the  id: "if-create-data-form". The id is important in order for the plugin to save the data to firebase.

.. code-block:: bash

    [contact-form-7 id="11" html_id="if-create-data-form" title="Contact form 1"]

.. figure:: /images/database/create-form.png
    :scale: 70%
    :align: center

    Sample form on frontend

After submitting, data will be saved to Firestore

.. figure:: /images/database/saved-to-firestore.png
    :scale: 70%
    :align: center

    Data saved to firestore

Example of creating new form and writing data to Realtime
----------------------------------

If you want to save data to Realtime database, the only thing that you need to change is the databaseType hidden field.

.. code-block:: bash

    [hidden databaseType "realtime"]

If there form is valid, the data will be saved to realtime database

.. figure:: /images/database/saved-to-realtime.png
    :scale: 70%
    :align: center

    Data saved to realtime

Addition Settings
----------------------------------

Contact form 7 comes with extra configurations. If you don't want to send a confirmation email to customers, you can this line to the addition settings.

.. code-block:: bash
    
    skip_mail: on

Reference
----------------------------------

https://contactform7.com/additional-settings/
https://contactform7.com/hidden-field/