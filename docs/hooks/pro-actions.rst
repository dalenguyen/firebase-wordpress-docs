Integrate Firebase PRO Action Hooks 
=============

Here is the list of action hooks that help to communicate with Firebase services.

After user successful logged in (v2.3.0)
----------------------------------

This action hook will trigger after user logged in successfully.


.. code-block:: php

    function example_callback($firebase_user) {
    // (maybe) do something with the $firebase_user.
    }
    
    add_action('firebase_after_user_successful_login', 'example_callback', 10, 1);