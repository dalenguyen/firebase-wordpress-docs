.. raw:: html

    <style> .red {color:red} </style>

Cloud Storage Integration
=============

At this stage, cloud storage is added to the plugin. However, in order to use it, you can follow the instruction or create your own scripts. If you can to customize it, please refer to the **Developer** section.

.. role:: red

    :red:`NOTE: Please don't implelement redirect on your form, it will interfere with file uploading process.`.

.. raw:: html

    <div style="position: relative; padding-bottom: 10%; height: 0; overflow: hidden; max-width: 100%; height: auto;">
        <iframe width="560" height="315" src="https://www.youtube.com/watch?v=NR4EcPirr4s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>

Enable Cloud Storage
----------------------------------

In general tab, you have add the **Storage Bucket** from your firebase project, then check the option for **Storage** under Firebase Services.

.. figure:: /images/storage/enable-cloud-storage.png
    :scale: 70%
    :align: center

    Configure Cloud Storage


Upload File to Cloud Storage
----------------------------------

Upload files to Cloud Storage is similar to Save Data to Firestore Database.

First, we need to create a form with the help of Contact Form 7 or you can design your own custom form if you want.

.. code-block:: bash

    // This form will create a path of the file to "users" collection
    // If you want to generate a random id, you can leave out the documentId
    // The file will be uploaded to "wpImages/documentId/timestamp+filename" path under Storage
    // Multiple files are separated by a comma ","

    [hidden collectionName "users"]
    [hidden documentId "some-random-id"]
    [hidden databaseType "firestore"]
    [hidden fileType "imageUrl1,imageUrl2"]

    [file imageUrl1 limit:1mb filetypes:gif|png|jpg|jpeg]
    [file imageUrl2 limit:1mb filetypes:gif|png|jpg|jpeg]

    [submit "Upload File"]

Please refer to the `Contact Form 7 <https://contactform7.com/file-uploading-and-attachment/>`_ for configuring your file input.

Then create a WordPress page / post to serve your form.

.. code-block:: bash

    // Add shortcode to your WordPress page / post 
    // Don't forget the html_id when you add the shortcode

    [contact-form-7 id="{{FORM-ID}}" html_id="if-create-data-form" title="{{FORM-TITLE}}"]

After submiting the file, it will be uploaded to Cloud Storage under **wpImages/som-random-id** path. The image name will be prefixed with a timestamp. For secuirty purpose, the image will be saved as a path. However, if you want to get the full readable URL, you can change the configuration. 


.. code-block:: bash

    // By adding `__public`, the file will be saved as full URL
    
    [hidden fileType "imageUrl__public"]
    ...
    ...
    [file imageUrl limit:1mb filetypes:gif|png|jpg|jpeg]

.. figure:: /images/storage/storage-images-path.png
    :scale: 70%
    :align: center

    Image Path in Storage

.. figure:: /images/storage/file-record-firestore.png
    :scale: 70%
    :align: center

    Image Path in Firestore