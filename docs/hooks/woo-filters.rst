Woocommerce Extension Filter Hooks 
=============

Here is the list of filter hooks that help to communicate with Firebase services.

Subscriptions - Before Subscription Status Updated
----------------------------------

This filter hook is called when the subscription status is updated (`woocommerce_subscription_status_updated`), before saving the subscription to the database.


.. code-block:: php

    add_filter('firebase_before_subscription_status_updated', 'edit_subscription_data_before_saving');

    function edit_subscription_data_before_saving($subscription) {
       // add custom data to user
       $subscription['custom_data'] = 'custom data 123';
       return $subscription;
    }



Subscriptions - Before Subscription Renewal Payment is Complete
----------------------------------

This filter hook is called when the subscription renewal payment is complete (`woocommerce_subscription_renewal_payment_complete`), before saving the subscription to the database.


.. code-block:: php

    add_filter('firebase_before_subscription_renewal_payment_complete', 'edit_subscription_data_before_saving');

    function edit_subscription_data_before_saving($subscription) {
       // add custom data to user
       $subscription['custom_data'] = 'custom data 123';
       return $subscription;
    }

Subscriptions - Before Saving Subscription to the Database
----------------------------------

This filter hook is called before saving subscription to firebase. This will call after `firebase_before_subscription_status_updated` and `firebase_before_subscription_renewal_payment_complete` filter hooks.


.. code-block:: php

    add_filter('firebase_before_save_subscription_to_firebase', 'edit_subscription_data_before_saving');

    function edit_subscription_data_before_saving($subscription) {
       // add custom data to user
       $subscription['custom_data'] = 'custom data 123';
       return $subscription;
    }

Membership - Before Saving Subscription to the Database (v2.11.0)
----------------------------------

This filter hook is called before saving membership to firebase.


.. code-block:: php

    add_filter('firebase_before_save_membership_to_firebase', 'edit_membership_data_before_saving');

    function edit_membership_data_before_saving($subscription) {
       // add custom data to user
       $membership['custom_data'] = 'custom data 123';
       return $membership;
    }