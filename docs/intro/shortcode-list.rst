List of Current Shortcodes
=============

Shortcodes are mostly used on WordPress frontend, when you create a page or a post in WordPress dashboard, you can embeded in the content.

.. code-block:: php

    // Page or Post

    [firebaseui_web][/firebaseui_web]

If you are a developer who knows PHP, you can use it anywhere you want. 

.. code-block:: php

    // php files

    echo do_shortcode("[firebaseui_web][/firebaseui_web]");

Authentication
----------------------------------

Demo: https://wordpress.dalenguyen.me/register-login-form/

.. code-block:: php

    // Add this shortcode in order show error message to the front end

    [firebase_error class='your-class-name'][/firebase_error]

.. code-block:: php

    // Login, Register through FirebaseUI Web
    // redirect parameter is optional

    [firebaseui_web redirect="link-to-page"][/firebaseui_web]

.. code-block:: php

    // After logging in, you will be redirect to the homepage. The redirect is optional. Default button text is "Login"

    [firebase_login button_text='Signin' redirect='/']

.. code-block:: php

    // Registration wilh extra fields: first name, last name and phone number. The redirect, extra fields and requried fields are optional. Without those, it will only show email and password fields.

    [firebase_register required_fields='firstName,lastName,phoneNumber' extra_fields='firstName,lastName,phoneNumber' redirect='/']

.. code-block:: php

    // Greetings Logged in User

    [firebase_greetings][/firebase_greetings]

.. code-block:: php

    // Logout Button
    // redirect after logging out and button_text are optional

    [firebase_logout redirect="/" button_text="Sign Out"][/firebase_logout]

Content
----------------------------------

.. code-block:: php

    // Show custom message for NOT Logged in Users

    [firebase_show_not_login class='your-class-name']YOUR HTML CODE[/firebase_show_not_login]

.. code-block:: php

    // Show custom message for Logged in Users

    [firebase_show class='your-class-name']YOUR HTML CODE[/firebase_show]

Realtime Database & Firestore
----------------------------------

**Note**: You can add html string to the field in the database in order to have an interactive field when displaying on WordPress.

Dynamically dispaly data from document:

- https://wordpress.dalenguyen.me/display-realtime-document-dynamically/
- https://wordpress.dalenguyen.me/display-firestore-document-dynamically/

In order to get data that relates to Firebase User Id, you can replace `document_name='some-string'` by  `document_name='getFirebaseUid'`. After user logs in, `getFirebaseUid` will be replaced by their user id.

**Realime collection as table**
`````````````

Demo: https://wordpress.dalenguyen.me/display-realtime-collection-data/

.. code-block:: php

    // show realtime collection data basing on collection name & display fields

    [realtime_col class='your-class-name' collection_name='users' display_fields='email,firstName,gender,food,hobbies,phone']

**Realime collection as blocks**
`````````````

Demo: https://wordpress.dalenguyen.me/display-realtime-collection-as-bocks/

.. code-block:: php

    // show realtime collection data basing on collection name & display fields
    // display fields or images is required

    [realtime_blocks class='your-class-name' collection_name='blog' display_fields='title,description,more' images='url']

    // In order to sort the data, you can add order_by, the order bases on orderByChild()

    [realtime_blocks class='your-class-name' collection_name='blog' display_fields='title,description,more' images='url' order_by='title']

**Realime Document as table**
`````````````

Demo: https://wordpress.dalenguyen.me/display-realtime-document-data/

.. code-block:: php

    // show realtime document data basing on collection name & document id as table
    // Collection & Document will be come path of the Realtime database --> /users/123456
    // display fields or images is required

    [realtime class='your-class-name' collection_name='string' document_name='string' display_fields='email,displayName,role,uid' images='imageUrl']

**Realime Document as blocks**
`````````````

Demo: https://wordpress.dalenguyen.me/display-realtime-document-data/

.. code-block:: php

    // show realtime document data basing on collection name & document id as blocks
    // Collection & Document will be come path of the Realtime database --> /users/123456
    // display fields or images is required

    [realtime class='your-class-name' collection_name='string' document_name='string' display_fields='email,displayName,role,uid' images='imageUrl' display_type='blocks']

**Firestore collection as table**
`````````````

Demo: https://wordpress.dalenguyen.me/display-firestore-collection-data/

.. code-block:: php

    // show firestore collection data basing on collection name & display fields
    // display fields or images is required
    // if you want to display document id, add `id` to display_fields


    [firestore_col class='your-class-name' collection_name='users' display_fields='email,firstName,gender,food,hobbies,phone']

**Firestore collection as blocks**
`````````````

Demo: https://wordpress.dalenguyen.me/display-firestore-collection-as-bocks/

.. code-block:: php

    // show firestore collection data basing on collection name & display fields
    // display fields or images is required
    // nested object key is also supported by using dot notation (e.g. author.fullName)

    // if you want to display document id, add `id` to display_fields


    [firestore_blocks class='your-class-name' collection_name='blog' display_fields='title,author.fullName,description,more' images='image.url']

    // In order to sort the data, you can add order_by. For example, this will order by title - descendant. You can also combine the orders: `order_by='title|asc,description|desc'`
    // You can also limit the data by adding a `limit` parameters (optional)

    [firestore_blocks class='your-class-name' collection_name='blog' display_fields='title,description,more' images='url' order_by='title|DESC' limit=10]

**Firestore collection through queries**
`````````````

Demo: https://wordpress.dalenguyen.me/display-firestore-with-queries/

In some cases, you have to open your console log and create an index for your queries.

.. code-block:: php

    // Operation list

    eq: '==',
    ne: '!=',
    gt: '>',
    ge: '>=',
    lt: '<',
    le: '<=',
    in: 'in',
    ni: 'not-in',
    ac: 'array-contains',
    aca: 'array-contains-any',

Sample Queries 

.. code-block:: php

    // Query 'users' collection
    // email == dale@dalenguyen.me
    // age > 20
    // display fields: email,firstName,lastName,age,gender
    // display as 'blocks' | 'table'

    [firestore_search class='your-class-name' search_fields='email|age' search_operators='eq|gt' search_conditions='dale@dalenguyen.me|20' collection_name='users' display_fields='email,firstName,lastName,age,gender' display_type='blocks']

    // In order to sort the data, you can add order_by. For example, this will order by title - descendant. You can also combine the orders: `order_by='firstName|asc,lastName|desc'`

In `search_conditions`, if you added getFirebaseUid, it will be replaced by Firebase UID after user logs in. 

**Firestore Document as table**
`````````````

Demo: https://wordpress.dalenguyen.me/display-firestore-document-data/

.. code-block:: php

    // show firestore data basing on collection name & document id
    // display fields or images is required
    // if you want to display document id, add `id` to display_fields

    [firestore class='your-class-name' collection_name='string' document_name='string' display_fields='email,displayName,role,uid' images='imageUrl']

**Firestore Document as blocks**
`````````````

Demo: https://wordpress.dalenguyen.me/display-firestore-document-data/

.. code-block:: php

    // show firestore data basing on collection name & document id
    // display fields or images is required
    // if you want to display document id, add `id` to display_fields


    [firestore class='your-class-name' collection_name='string' document_name='string' display_fields='email,displayName,role,uid' images='imageUrl' display_type='blocks']

Custom Claims (User's roles)
----------------------------------

Demo: https://wordpress.dalenguyen.me/show-or-hide-content-for-logged-in-users/

.. code-block:: php

    // only user with admin claim will see the content
    // otherwise they will see a Custom message

    [firebase_show_with_claims class='your-class-name' claims='admin' message='Custom message' ] HTML Data With Tags [/firebase_show_with_claims]
