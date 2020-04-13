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

.. code-block:: php

    // Login, Register through FirebaseUI Web
    [firebaseui_web][/firebaseui_web]

.. code-block:: php

    // Greetings Logged in User
    [firebase_greetings][/firebase_greetings]

.. code-block:: php

    // Show Firebase Error
    [firebase_error class='your-class-name'][/firebase_error]

.. code-block:: php

    // Logout Button
    [firebase_logout][/firebase_logout]

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

**Realime collection**

Demo: https://wordpress.dalenguyen.me/display-realtime-collection-data/

.. code-block:: php

    // show realtime collection data basing on collection name & display fields
    [realtime_col class='your-class-name' collection_name='users' display_fields='email,firstName,gender,food,hobbies,phone']

**Realime Document**

Demo: https://wordpress.dalenguyen.me/display-realtime-document-data/

.. code-block:: php

    // show realtime document data basing on collection name & document id
    [realtime class='your-class-name' collection_name='string' document_name='string']

**Firestore collection**

Demo: https://wordpress.dalenguyen.me/display-firestore-collection-data/

.. code-block:: php

    // show firestore collection data basing on collection name & display fields
    [firestore_col class='your-class-name' collection_name='users' display_fields='email,firstName,gender,food,hobbies,phone']

**Firestore Document**

Demo: https://wordpress.dalenguyen.me/display-firestore-document-data/

.. code-block:: php

    // show firestore data basing on collection name & document id
    [firestore class='your-class-name' collection_name='string' document_name='string']

Custom Claims (User's roles)
----------------------------------

Demo: https://wordpress.dalenguyen.me/show-or-hide-content-for-logged-in-users/

.. code-block:: php

    // only user with admin claim will see the content
    // otherwise they will see a Custom message
    [firebase_show_with_claims class='your-class-name' claims='admin' message='Custom message' ] HTML Data With Tags [/firebase_show_with_claims]
