Integrate Firebase PRO Filter Hooks 
=============

Here is the list of filter hooks that help to communicate with Firebase services.

Get data from Firebase (v2.3.0)
----------------------------------

This filter hook will help to get data from Firebase (Realtime or Firestore).


.. code-block:: php

    /**
    * Get Data from Firebase Database
    *
    * @param [type] $database_type realtime | firestore
    * @param [type] $collection_name
    * @param [type] $doc_id
    * @return data | false
    */

    // start saving data to firebase
    apply_filters('firebase_get_data_from_database', $database_type, $collection_name, $doc_id);

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