Firebase Filter Hooks 
=============

Here is the list of filter hooks that help to communicate with Firebase services.

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