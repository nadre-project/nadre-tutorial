Search Engine API
=================

.. sidebar:: Table of content

  * `1. Introduction`_
  * `2. XML API`_

    * `2.1 Get records`_
    * `2.2 Look for patterns in fields`_
    * `2.3 Filter records and outputs`_
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

----------------
2. XML API
----------------

To get results of your queries in XML format you have to set output format parameter to **xm** (:code:`of=xm`). The OAR return the results in MARCXML [#]_.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
2.1 Get records
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

So, to get the first 10 records stored in the OAR in XML format you can use the following query

.. raw:: html

    <embed>
        <a href="http://nadre.ethernet.edu.et/search?jrec=1&rg=10&of=xm" target="_blank">http://nadre.ethernet.edu.et/search?jrec=1&rg=10&of=xm</a>
    </embed>

You can change :code:`jrec` parameter to implement records pagination, for example the query:

.. raw:: html

    <embed>
        <a href="http://nadre.ethernet.edu.et/search?jrec=11&rg=10&of=xm" target="_blank">http://nadre.ethernet.edu.et/search?jrec=11&rg=10&of=xm</a>
    </embed>

returns the next 10 records starting from the eleventh, or use the following

.. raw:: html

    <embed>
      <a href="http://nadre.ethernet.edu.et/search?jrec=21&rg=10&of=xm" target="_blank">http://nadre.ethernet.edu.et/search?jrec=21&rg=10&of=xm</a>
    </embed>

to get records from 21\ :sup:`st` to 30\ :sup:`th`, and so on...

.. warning::

  Do not set `rg` too high; there is a server-wide safety limit on it.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
2.2 Look for patterns in fields
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To get, for example, the first 10 records that contains the string *'Hackfest'*, you can use the :code:`p` parameter to specify the pattern you are looking for and :code:`f` parameter to specify the field in which search the patter. See the query below:

.. raw:: html

    <embed>
      <a href="http://nadre.ethernet.edu.et/search?p=Hackfest&f=title&jrec=0&rg=10&of=xm" target="_blank">http://nadre.ethernet.edu.et/search?p=Hackfest&f=title&jrec=0&rg=10&of=xm</a>
    </embed>

Where
  **p** is pattern (e.g. your query)

  **f** is field to search within (e.g. “title”, “authors”..)

If you want to get, for example, the first 10 records in *'PRESENTATIONSNADRE'* collection that contains *'NADRE'* in keyword, you can use:

.. raw:: html

    <embed>
      <a href="http://nadre.ethernet.edu.et/search?p1=collection:PRESENTATIONSNADRE+keyword:NADRE&of=xm&jrec=1&rg=10" target="_blank"> http://nadre.ethernet.edu.et/search?p1=collection:PRESENTATIONSNADRE+keyword:NADRE&of=xm&jrec=1&rg=10</a>
    </embed>

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
2.3 Filter records and outputs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To get all records uploaded from a given date (e.g. 2018-01-01) to another given date (e.g. 2018-02-22), you can issue:

.. raw:: html

    <embed>
      <a href="http://nadre.ethernet.edu.et/search?of=xm&d1=2018-01-01&d2=2018-02-22" target="_blank"> http://nadre.ethernet.edu.et/search?of=xm&d1=2018-01-01&d2=2018-02-22</a>
    </embed>

Where
  **d1** is the first date in `YYYY-mm-dd` format

  **d2** is the first date in `YYYY-mm-dd` format

.. You can also filter the OAR results specifing only the fileds in you are interested in, for example to get only the abstract, title and authors of  resources, use the following query:

.. .. raw:: html

    <embed>
      <a href="http://nadre.ethernet.edu.et/search?of=xm&ot=abstract,title,authors" target="_blank"> http://nadre.ethernet.edu.et/search?of=xm&ot=abstract,title,authors</a>
    </embed>

.. Where
  **ot** output tags, is a comma separated lists of tags should be shown (e.g. ‘’ to get all fields, ‘title’ to get titles only).

------------
JSON API
------------

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur semper, augue et accumsan pulvinar, orci augue fringilla ligula, vitae hendrerit mi neque ac diam. Nam a facilisis ligula. Nunc sit amet velit non dui bibendum suscipit malesuada non ex. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Fusce fermentum nulla finibus, scelerisque mauris et, egestas metus. Pellentesque ut finibus ipsum. Phasellus pharetra tristique mi, vitae facilisis neque lacinia sit amet. Donec odio odio, porta at vehicula ut, vehicula ut enim. Cras congue sapien at metus vestibulum, eu vehicula enim imperdiet. Aliquam erat volutpat. Nulla ullamcorper ipsum

.. topic:: Before proceeding...

  You need to have some useful tools used in the rest of this tutorial:
   - :code:`curl` a tool to transfer data from or to a server `link  <http://www.mit.edu/afs.new/sipb/user/ssen/src/curl-7.11.1/docs/curl.html>`_;
   - :code:`jq` a lightweight and flexible command-line JSON processor `link <https://stedolan.github.io/jq/>`_;
   - :code:`php5-cli` and :code:`php5-curl`

----------
References
----------

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur semper, augue et accumsan pulvinar, orci augue fringilla ligula, vitae hendrerit mi neque ac diam. Nam a facilisis ligula. Nunc sit amet velit non dui bibendum suscipit malesuada non ex. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Fusce fermentum nulla finibus, scelerisque mauris et, egestas metus. Pellentesque ut finibus ipsum. Phasellus pharetra tristique mi, vitae facilisis neque lacinia sit amet. Donec odio odio, porta at vehicula ut, vehicula ut enim. Cras congue sapien at metus vestibulum, eu vehicula enim imperdiet. Aliquam erat volutpat. Nulla ullamcorper ipsum

.. [#] http://nadre.ethernet.edu.et/help/hacking/search-engine-api
.. [#] http://nadre.ethernet.edu.et/help/admin/howto-marc
