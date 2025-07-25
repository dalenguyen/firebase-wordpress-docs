Integrate Firebase PRO Filter Hooks 
=============

Here is the list of filter hooks that help to communicate with Firebase services.

Get data from Firebase (v2.3.0)
----------------------------------

This filter hook will help to get document data from Firebase (Realtime or Firestore).


.. code-block:: php

    /**
    * Get Data from Firebase Database
    *
    * @param [type] $database_type realtime | firestore
    * @param [type] $collection_name
    * @param [type] $doc_id
    * @return data | false
    */

    // start getting data to firebase
    apply_filters('firebase_get_data_from_database', $database_type, $collection_name, $doc_id);

Get data from Firebase (v3.31.0)
----------------------------------

This filter hook will help to get collection data from Firebase (Firestore).


.. code-block:: php

    /**
    * Get Data from Firebase Database
    *
    * @param [type] $database_type firestore
    * @param [type] $collection_name
    * @return data | false
    */

    // start getting data to firebase
    apply_filters('firebase_get_collection_from_database', 'firestore', '$collection_name);


Update Doc Id before saving to Firebase (v2.16.0)
----------------------------------

This filter hook will allow to modify document id before saving data to firebase. The use case is when you have multiple WordPress websites that utilize Firebase authentication. If you choose to sync data (posts or WooCommerce Subscriptions), the id of those data will overridden which causes issues for your users. It's better to utilize this filter hook to create a unique document id for each site before saving to firebase. 

.. code-block:: php

    add_filter('firebase_update_doc_id_before_saving_to_database', 'update_doc_id_before_saving_to_database', 10, 2);

    function update_doc_id_before_saving_to_database($collection_name, $doc_id) {
        // transform doc_id if collection name is subscriptions
        if ($collection_name == 'subscriptions') {
            // Remove http:// or https:// before returning new id
            $new_doc_id = $doc_id . '-' . preg_replace('#^[^:/.]*[:/]+#i', '', get_site_url());
            // example of new document id: 144-example.com
            return $new_doc_id;
        }

        // return default doc_id if condition doesn't match
        return $doc_id;
    }


Before Saving Post data to Firebase
----------------------------------

This filter hook will help to modify post data before saving to Firebase. This will also apply to custom post types. If you want to save user data manually, you can use `Save data to Firebase` filter hook.


.. code-block:: php

    add_filter('firebase_before_saving_post_to_database', 'edit_post_data_before_saving');

    function edit_post_data_before_saving($post) {
       // add custom data to post
       $post->custom_data = 'custom data 123';
       return $post;
    }


Before Saving User data to Firebase
----------------------------------

This filter hook will help to modify User data before saving to Firebase. It will happen only once where user first login to the site. If you want to save user data manually, you can use `Save data to Firebase` filter hook.


.. code-block:: php

    add_filter('firebase_before_saving_user_to_database', 'edit_user_data_before_saving');

    function edit_user_data_before_saving($user) {
       // add custom data to user
       $user['custom_data'] = 'custom data 123';
       return $user;
    }

Save data to Firebase
----------------------------------

This filter hook will help to save data from WordPress to Firebase (Realtime or Firestore).


.. code-block:: php

    /**
    * Send Data to Firebase Database
    *
    * @param [type] $database_type realtime | firestore
    * @param [type] $collection_name
    * @param [type] $doc_id
    * @param [type] $data object
    * @return boolean
    */

    // start saving data to firebase
    apply_filters('firebase_save_data_to_database', $database_type, $collection_name, $doc_id, $data);

Delete data from Firebase
----------------------------------

This filter hook will help to delete data from Firebase (Realtime or Firestore).


.. code-block:: php

    /**
    * Delete Data from Firebase Database
    *
    * @param [type] $database_type realtime | firestore
    * @param [type] $collection_name
    * @param [type] $doc_id
    * @return boolean
    */

    // start delete data from firebase
    apply_filters('firebase_delete_data_from_database', $database_type, $collection_name, $doc_id);

Create New User in Firebase (v3.21.0)
----------------------------------

This filter hook allows you to create a new user in Firebase when a WordPress user is registered. This is useful when you want to automatically create Firebase users for new WordPress registrations.

.. code-block:: php

    /**
    * Create New User in Firebase
    *
    * @param int $user_id WordPress user ID
    * @param array $user_data User data array containing email, first_name, last_name, password
    * @return void
    */

    public static function user_register_event($user_id, $user) {
        // Example user data structure:
        // [29-Oct-2022 08:54:29 UTC] Array
        // (
        //     [first_name] => Test
        //     [last_name] => 500
        //     [user_login] => test500
        //     [user_pass] => xxx
        //     [user_email] => test500@dalenguyen.me
        //     [role] => customer
        // )

        $firebase_uid = get_user_meta($user_id, 'firebase_uid', true);

        // Normal flow only has email & password in the $user
        // Consider using wp_insert_user to have custom data in the fields which 
        // will help in case of passing meta data (firebase_uid...)
        if (empty($firebase_uid) && isset($user['first_name'])) {
            // Prepare user data for Firebase
            $user_data = array(
                'uid' => uniqid('wp_', true), // OPTIONAL:Generate custom Firebase UID or fallback
                'email' => $user['user_email'],
                'displayName' => trim($user->first_name . ' ' . $user->last_name),
                'password' => $user['user_pass'],
            );

            // Create user in Firebase
            apply_filters('firebase_create_new_user', $user_id, $user_data);
        }
    }

    // Hook into WordPress user registration
    add_action('user_register', 'user_register_event', 10, 2);

Update Custom Error Messages
----------------------------------

This filter hook will help to update error messages for the plugin. 

Demo: https://youtu.be/JjeF7QY7M_0


.. code-block:: php

    add_filter('firebase_edit_public_translation_texts', 'edit_public_translation_texts');
    
    function edit_public_translation_texts($texts) {
       $texts['auth']['emailPasswordMissing'] = 'Please enter email and password';
       $texts['auth']['auth/user-not-found'] = 'User is not found. <a href="https://google.com">Click here</a> to register.';
       return $texts;
    }
