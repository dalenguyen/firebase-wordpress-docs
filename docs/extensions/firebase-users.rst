.. raw:: html

    <style> .red {color:red} .green {color: green} </style>

Integrate Firebase Users
=============

.. role:: red

:red:`This is not a standalone product. In order to use this extension, you need to install at least Integrate Firebase PRO (v1.21.0) and Firebase WordPress functions (v0.15.0).`

.. role:: red

:red:`**IMPORTANT WARNING:** For WordPress versions that support bcrypt encryption (since WordPress 6.8), users are imported but you need to implement an email service to send password reset links to the users. If you need to send password reset links, please contact me for further support.`

The sole purpose of this plugin is to help web masters to migrate WordPress users to Firebase. **This should be done one in production to avoid users duplication!**

Install the extension
----------------------------------

After downloading the extension, you can install and active the plugin. You will find it under **Firebase > Import Users**.

.. figure:: /images/extensions/firebase-users/active-firebase-users.png
    :scale: 70%
    :align: center

    Active Firebase Users plugin 

As you can see, there is 159 users in WordPress

Import WordPress Users to Firebase
----------------------------------

In order to import WordPress users to Firebase, you just need to press the button **Import WP Users to Firebase**, and the plugin will do its magic.

.. role:: note

:green:`If you have more than 10,000 users, please try to increase max_execution_time & memory_limit in PHP. If it still doesn't work, please contact me for further support.`


The Firebase UID will be the WordPress **user_login**. It's because if uid is generated randomly, it will create another user with the same email. You can have a look the `Firebase Docs <https://firebase.google.com/docs/auth/admin/import-users#usage>`_ .

.. role:: note

:red:`Please note that if users don't have an email, it will not be imported to Firebase.`

.. figure:: /images/extensions/firebase-users/successfully-import-wordpress-users.png
    :scale: 70%
    :align: center

    Successfully imported Users from WordPress to Firebase

I recommend that you should try the plugin in your local machine or development environment before moving to production.

Import a Single User to Firebase
----------------------------------

If you need to import just one specific user to Firebase instead of all users, you can modify the import process. This is useful when you want to test the import functionality or add individual users.

**Method 1: Get Current Logged-in User**

Instead of querying the database, you can get the currently logged-in user using WordPress's built-in function:

````php
// Get the current logged-in user
$current_user = wp_get_current_user();

if ($current_user->exists()) {
    // Create an array with just the current user
    self::$users = array($current_user);
    
    // Run the import process
    $resObj = apply_filters('firebase_import_users_to_firebase', self::$users);
    
    if ($resObj->status) {
        echo 'Successfully imported current user: ' . $current_user->user_email;
    } else {
        echo 'Error importing user: ' . $resObj->message;
    }
} else {
    echo 'No user is currently logged in.';
}
````

**Method 2: Query by Specific Criteria**

Alternatively, you can modify the user query to target a specific user by their ID, email, or username:

**By User ID:**
````php
// Instead of: SELECT * from $wpdb->users WHERE NULLIF(user_email, '') IS NOT NULL
$user_id = 123; // Replace with the actual user ID
self::$users = $wpdb->get_results("SELECT * from $wpdb->users WHERE ID = $user_id AND NULLIF(user_email, '') IS NOT NULL");
````

**By Email Address:**
````php
$user_email = 'user@example.com'; // Replace with the actual email
self::$users = $wpdb->get_results($wpdb->prepare("SELECT * from $wpdb->users WHERE user_email = %s AND NULLIF(user_email, '') IS NOT NULL", $user_email));
````

**By Username:**
````php
$username = 'john_doe'; // Replace with the actual username
self::$users = $wpdb->get_results($wpdb->prepare("SELECT * from $wpdb->users WHERE user_login = %s AND NULLIF(user_email, '') IS NOT NULL", $username));
````

After modifying the query, run the import process as usual. The plugin will only import the user(s) that match your criteria.

.. role:: note

:red:`Remember to revert the query back to the original after importing the single user to avoid affecting future bulk imports.`

.. role:: note

:green:`Getting the current logged-in user is the simplest method for testing the import functionality.`

Firebase Import Implementation Example
----------------------------------

The actual Firebase import is handled through a filter hook. Here's how the import process works:

````php
public static function firebase_start_to_import_users() {
    // Verify nonce for security
    $firebaseUsersNonce = $_POST['firebaseUsersNonce'];
    
    if (!wp_verify_nonce($firebaseUsersNonce, 'firebaseUsers')) {
        die(__('Firebase - Security check failed', 'ifp-users'));
    }
    
    echo 'Start importing process...<br>';
    
    // Process users in chunks of 1000 to avoid memory issues
    $user_chunks = array_chunk(self::$users, 1000);
    
    foreach ($user_chunks as $user_chunk) {
        echo '<p>Importing ' . count($user_chunk) . ' users...</p>';
        
        // This is where the actual Firebase import happens
        $resObj = apply_filters('firebase_import_users_to_firebase', $user_chunk);
        
        if ($resObj->status) {
            echo $resObj->message;
        } else {
            echo 'Error: ' . $resObj->message;
            error_log(print_r($resObj, true));
        }
        
        // Wait 3 seconds between chunks to avoid rate limiting
        sleep(3);
    }
    
    exit("Finished migrating users to Firebase!");
}
````

The `firebase_import_users_to_firebase` filter is implemented in the **Integrate Firebase PRO** plugin and handles:

1. **User Data Preparation**: Converts WordPress user objects to Firebase user format
2. **Firebase Authentication**: Creates users in Firebase Auth using the Admin SDK
3. **Custom Claims**: Sets any custom claims if configured
4. **Error Handling**: Returns success/error status and messages

The Firebase UID will be the WordPress **user_login** to avoid creating duplicate users with the same email address.

.. role:: note

:green:`The import process automatically handles user data conversion, Firebase authentication, and error reporting. You don't need to implement the Firebase import logic yourself.`