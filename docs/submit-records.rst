Submit
======

.. sidebar:: Table of content

  * `Introduction`_
  * `cURL`_

    * :ref:`sub-label1`
  * `PHP`_

    * :ref:`sub-label2`

.. _`Introduction`:

Introduction
------------
This section will show you how to upload records to the NADRE repository through :code:`curl` command and some sample :code:`php` script.

All the examples are colleted in the submit folder, you can find them  in the github repository (`link <https://github.com/nadre-project/nadre-tutorial/tree/master/submit>`_). This folder consists of four subfolders:

1. :code:`/asset` folder contains the sample objects used in the examples;

2. :code:`/curl` folder consists of some :code:`.md` files that have the command to perform to upload file to the OAR repository and the expected output;

3. :code:`/php` folder has a set of simple php scripts to upload files to NADRE repository;

4. :code:`/xml` folder contains the MARCXML files that describe the resources are going to be uploaded.

.. _`cURL`:

cURL
------------

The cURL example are stored in the github repository curl `subfolder  <https://github.com/nadre-project/nadre-tutorial/tree/master/submit/curl>`_. It has several :code:`<digital-object>-submission-to-OAR.md` files with curl command to upload image, dataset, publication, etc. and the expected output repository will return.
Then it contains also a Pyhton script (:code:`request_doi.py`) to generate a DOI based on the system timestamp, is mandatory, before to upload any digital object to the repository, performing this script to reserve a valid DOI and replace it in the corresponding :code:`<digital-object>-submission-to-OAR.xml` inside the :code:`/xml` folder.

.. _`sub-label1`:

Image upload
^^^^^^^^^^^^
From the downloaded github repository folder, change to the :code:`/submit/curl/` sub-folders with:

.. code-block:: bash

	nadre-tutorial-master$ cd submit/curl

To upload an image, for example, to the NADRE repository, you can refer to the :code:`image-submission-to-OAR.md` file shown below.

.. literalinclude:: files/image-submission-to-OAR.md
	:language: bash

That contains the curl command to perform and the expected output.

.. _`create_doi`:

Step 1: Create new DOI
~~~~~~~~~~~~~~~~~~~~~~
First of all, you have to create a new DOI executing the :code:`request_doi.py` script, as follows:

.. code-block:: bash

	nadre-tutorial-master/submit/curl$ python request_doi.py

.. _`edit_xml`:

Step 2: Edit XML file
~~~~~~~~~~~~~~~~~~~~~
Now edit the :code:`../xml/image-submission-to-OAR.xml` file with your favourite editor. As example:

1. edit the placeholder in the :code:`tag="024"` with the DOI generated above

.. literalinclude:: files/image-submission-to-OAR.xml
	:language: xml
	:lines: 3-7

2.  edit the publication date in the :code:`tag="260"`

.. literalinclude:: files/image-submission-to-OAR.xml
	:language: xml
	:lines: 8-10

3. the image **main author** in the :code:`tag="100"` (use the :code:`tag="700"` for other authors), specifing the
	* Author name in :code:`code="a"`
	* Affiliation in :code:`code="v"`
	* Country in :code:`code="w"`
	* ORCID in :code:`code="j"`

.. literalinclude:: files/image-submission-to-OAR.xml
	:language: xml
	:lines: 11-16

3. then specify the publication keywords in the :code:`tag="653"`, you can create several :code:`tag="653"` as many as keywords you want specify

.. literalinclude:: files/image-submission-to-OAR.xml
	:language: xml
	:lines: 36-41

4. another important filed you have to edit is the :code:`tag="FFT"` that represents where the resource can be found

.. literalinclude:: files/image-submission-to-OAR.xml
	:language: xml
	:lines: 52-54

.. note::

	Have a look at `this link <https://nadre.ethernet.edu.et/help/admin/howto-marc>`_ to know more about MARCXML tag meaning.

Step 3: Submit record
~~~~~~~~~~~~~~~~~~~~~

Once you completed to edit the xml file, perform the following command to actually upload the file:

.. code-block:: bash

	curl -T ../xml/image-submission-to-OAR.xml \
	http://nadre.ethernet.edu.et/batchuploader/robotupload/insert \
	-A invenio_webupload -H "Content-Type: application/marcxml+xml"

If everything's went well it returns something like:

.. code-block:: bash

	[INFO] bibupload batchupload --insert /opt/invenio/var/tmp-shared/batchupload_20161122(...)

an email will inform NADRE repository administrators of your your new submission then, after they review it, will actually publish the new record on the OAR.

.. _`PHP`:

PHP
------------

This section shows you how to upload file to NADRE repository through simple PHP scripts. PHP examples are stored in the github repository :code:`/php` `here  <https://github.com/nadre-project/nadre-tutorial/tree/master/submit/php>`_. It contains several :code:`<digital-object>-submission-to-OAR.php` files with demostrative php code, that uses the php `Client URL library <http://php.net/manual/en/book.curl.php>`_ to upload resources. As we saw in the previous section, is mandatory to generate a DOI, to do so you can use :code:`request_doi.py` script in :code:`/curl` folder, while the xml filer that describe the resources are located in the :code:`/xml` one.


.. _`sub-label2`:

Presentation upload
^^^^^^^^^^^^^^^^^^^

From the downloaded github repository folder, change to the :code:`/submit/php/` sub-folders with:

.. code-block:: bash

	nadre-tutorial-master$ cd submit/php

Now we will see how to upload a presentation, to the NADRE repository, so you can refer to the :code:`presentation-submission-to-OAR.php` file shown below.

.. literalinclude:: files/presentation-submission-to-OAR.php
	:language: php

As you can see it accept a parameter that is the repository hostname and will notify the user if no hostname is specified.


Step 1: Create new DOI
~~~~~~~~~~~~~~~~~~~~~~
See :ref:`create_doi`

Step 2: Edit XML file
~~~~~~~~~~~~~~~~~~~~~
Now edit the :code:`../xml/presentation-submission-to-OAR.xml` file with your favourite editor. See :ref:`edit_xml` to edit the MARCXML tags as you need

Step 3: Submit record
~~~~~~~~~~~~~~~~~~~~~

.. note::

	To actually submit the new record we will use PHP form the command line interface, you can install it using the packaged distribution of php-cli for ypu operating system.

	As example for an Ubuntu based machine you can install php-cli with the following command

	.. code-block:: bash

		sudo apt-get install php5-cli

Once you finished to edit the XML file you can submit the new presentation using the following command

.. code-block:: bash

	php presentation-submission-to-OAR.php nadre.ethernet.edu.et

The output you'll get, if everything went well, is the same you saw in previous section and at the same way the administrator will receive an email to notify that a new record have to be revised to be published.
