Search Engine API
=================

.. sidebar:: Table of content

  * `Introduction`_
  * `XML API`_
  * `JSON API`_
  * `References`_

------------
Introduction
------------

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

.. [#] http://nadre.ethernet.edu.et/help/hacking/search-engine-api

----------------
XML API
----------------

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur semper, augue et accumsan pulvinar, orci augue fringilla ligula, vitae hendrerit mi neque ac diam. Nam a facilisis ligula. Nunc sit amet velit non dui bibendum suscipit malesuada non ex. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Fusce fermentum nulla finibus, scelerisque mauris et, egestas metus. Pellentesque ut finibus ipsum. Phasellus pharetra tristique mi, vitae facilisis neque lacinia sit amet. Donec odio odio, porta at vehicula ut, vehicula ut enim. Cras congue sapien at metus vestibulum, eu vehicula enim imperdiet. Aliquam erat volutpat. Nulla ullamcorper ipsum

^^^^^^^^^^^^^^^^
Paginate results
^^^^^^^^^^^^^^^^

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur semper, augue et accumsan pulvinar, orci augue fringilla ligula, vitae hendrerit mi neque ac diam. Nam a facilisis ligula. Nunc sit amet velit non dui bibendum suscipit malesuada non ex. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Fusce fermentum nulla finibus, scelerisque mauris et, egestas metus. Pellentesque ut finibus ipsum. Phasellus pharetra tristique mi, vitae facilisis neque lacinia sit amet. Donec odio odio, porta at vehicula ut, vehicula ut enim. Cras congue sapien at metus vestibulum, eu vehicula enim imperdiet. Aliquam erat volutpat. Nulla ullamcorper ipsum

------------
JSON API
------------

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur semper, augue et accumsan pulvinar, orci augue fringilla ligula, vitae hendrerit mi neque ac diam. Nam a facilisis ligula. Nunc sit amet velit non dui bibendum suscipit malesuada non ex. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Fusce fermentum nulla finibus, scelerisque mauris et, egestas metus. Pellentesque ut finibus ipsum. Phasellus pharetra tristique mi, vitae facilisis neque lacinia sit amet. Donec odio odio, porta at vehicula ut, vehicula ut enim. Cras congue sapien at metus vestibulum, eu vehicula enim imperdiet. Aliquam erat volutpat. Nulla ullamcorper ipsum

----------
References
----------

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur semper, augue et accumsan pulvinar, orci augue fringilla ligula, vitae hendrerit mi neque ac diam. Nam a facilisis ligula. Nunc sit amet velit non dui bibendum suscipit malesuada non ex. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Fusce fermentum nulla finibus, scelerisque mauris et, egestas metus. Pellentesque ut finibus ipsum. Phasellus pharetra tristique mi, vitae facilisis neque lacinia sit amet. Donec odio odio, porta at vehicula ut, vehicula ut enim. Cras congue sapien at metus vestibulum, eu vehicula enim imperdiet. Aliquam erat volutpat. Nulla ullamcorper ipsum
