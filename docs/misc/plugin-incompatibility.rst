Incompatible Plugins
=============

Here is the list of plugins that may not work with **Integrate Firebase PRO**

Redirection for Contact Form 7
----------------------------------

If are using Contact Form 7 in order to save data to Firebase, you shouldn't implement redirect method. It's because the syncing process happens at the same time with contact form 7. If the page redirects too early, the process is not probably finished yet. 

JWT Auth
----------------------------------


The issue is  JWT Auth requires Authorization in the headers. You have to whitelist the endpoint `'/wp-json/firebase/v2/*'`

Check this `Github Issue <https://github.com/dalenguyen/firebase-wordpress-plugin/issues/180>`_  for solution.