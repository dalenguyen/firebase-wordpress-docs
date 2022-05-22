.. raw:: html

    <style> .red {color:red} </style>

Video Chat (Beta)
=============

This extension is a beta version. If you are using the PRO > v3.12.1, you can give this one a try. 

`Download Link <https://drive.google.com/drive/folders/10qn9sUD-jOdtE40F6NCgsWh5X8qA4NOY?usp=sharing>`_

This extension will support 1-on-1 video chat.

Demo: https://wordpress.dalenguyen.me/video-chat-beta/

Prerequisites
----------------------------------

Update firestore security rules

.. code-block:: bash

    // RTC - START
    match /rooms/{room} {
        allow read, write: if request.auth != null;
        
        match /calleeCandidates/{candidate} {
      		allow read, write: if request.auth != null;
        }
        
         match /callerCandidates/{candidate} {
      		allow read, write: if request.auth != null;
        }
    }
    // RTC - END