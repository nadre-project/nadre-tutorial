Search Engine API
=================

.. sidebar:: Table of content

  * `1. Introduction`_
  * `2. XML API`_

    * `2.1 Get records`_
    * `2.2 Look for patterns in fields`_
  * `JSON API`_
  * `References`_

---------------
1. Introduction
---------------

Exploiting search Engine API of an Invenio based OAR allows you to create, for example, a new front end for your repository.
To search or browse records in the OAR you have to just create HTML queries specifing the list of parameters, that allow users to find the records in which they are interested in, so you can present the results in a nicer interface.

Following the syntax should be used to create the queries:

Syntax
  .. code-block:: bash

    GET /search?p=...&of=...&ot=...&jrec=...&rg=...

where
  **p** is pattern (i.e. your query)

  **of** is output format (e.g. `xm` for MARCXML)

  **ot** is output tags (e.g. `` to get all fields, `100` to get titles only)

  **jrec** is jump to record ID (e.g. 1 for first hit)

  **rg** is records-in-groups-of (e.g. 10 hits per page)

You can use other parameters as well; the list above mentions the most useful one.  For full documentation on these and the other `/search` URL parameters, please see section 3.1 of Search Engine API [#]_.

.. topic:: Before proceeding...

  You need to have some useful tools used in the rest of this tutorial:
   - :code:`curl` a tool to transfer data from or to a server `link  <http://www.mit.edu/afs.new/sipb/user/ssen/src/curl-7.11.1/docs/curl.html>`_;
   - :code:`jq` a lightweight and flexible command-line JSON processor `link <https://stedolan.github.io/jq/>`_;
   - :code:`php5-cli` and :code:`php5-curl`

----------------
2. XML API
----------------

To get results of your queries in XML format you have to set output format parameter to **xm** (:code:`of=xm`). The OAR return the results in MARCXML [#]_.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
2.1 Get records
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

So, to get the first 10 records stored in the OAR in XML format you can do

.. code-block:: bash

  curl -X GET \
  'http://nadre.ethernet.edu.et/search?jrec=1&rg=10&of=xm'

You can change :code:`jrec` parameter to implement records pagination, issue

.. code-block:: bash

  curl -X GET \
  'http://nadre.ethernet.edu.et/search?jrec=11&rg=10&of=xm'

to get the next 10 records starting from the eleventh, or

.. code-block:: bash

  curl -X GET \
  'http://nadre.ethernet.edu.et/search?jrec=21&rg=10&of=xm'

to get records from 21:sup:`st` to 30:sup:`th`, and so on...

.. warning::

  Do not set `rg` too high; there is a server-wide safety limit on it.

------------------------------------
2.2 Look for patterns in fields
------------------------------------



------------
JSON API
------------

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur semper, augue et accumsan pulvinar, orci augue fringilla ligula, vitae hendrerit mi neque ac diam. Nam a facilisis ligula. Nunc sit amet velit non dui bibendum suscipit malesuada non ex. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Fusce fermentum nulla finibus, scelerisque mauris et, egestas metus. Pellentesque ut finibus ipsum. Phasellus pharetra tristique mi, vitae facilisis neque lacinia sit amet. Donec odio odio, porta at vehicula ut, vehicula ut enim. Cras congue sapien at metus vestibulum, eu vehicula enim imperdiet. Aliquam erat volutpat. Nulla ullamcorper ipsum

----------
References
----------

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur semper, augue et accumsan pulvinar, orci augue fringilla ligula, vitae hendrerit mi neque ac diam. Nam a facilisis ligula. Nunc sit amet velit non dui bibendum suscipit malesuada non ex. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Fusce fermentum nulla finibus, scelerisque mauris et, egestas metus. Pellentesque ut finibus ipsum. Phasellus pharetra tristique mi, vitae facilisis neque lacinia sit amet. Donec odio odio, porta at vehicula ut, vehicula ut enim. Cras congue sapien at metus vestibulum, eu vehicula enim imperdiet. Aliquam erat volutpat. Nulla ullamcorper ipsum

.. [#] http://nadre.ethernet.edu.et/help/hacking/search-engine-api
.. [#] http://nadre.ethernet.edu.et/help/admin/howto-marc
