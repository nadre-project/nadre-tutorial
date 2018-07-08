# Search Engine API

Invenio has a Search Engine API, you can use to find what you are looking for.

* Syntax: `GET /search?p=...&of=...&ot=...&jrec=...&rg=...`

To get the full list of available parameters you can have a look at the [Search Engine API documentation](https://nadre.ethernet.edu.et/help/hacking/search-engine-api).

## Examples

Invenio provides three different kinds of API

1. XML API
2. JSON API
3. Pyhton API

In the following sections you will see [XML API](#xmlapi) and then [JSON API](#jsonapi). You can use these examples by coping the URL in your browser, and replacing the placeholder `${API_ENDPOINT}` with the actual Invenio based OAR endpoint. Otherwise you can can use the [curl](http://www.mit.edu/afs.new/sipb/user/ssen/src/curl-7.11.1/docs/curl.html) command line tool.

### <a name="xmlapi" />XML API

Using these APIs will return results in XML format.

#### Get first 10 records in the OAR

The following is the query to get the first 10 in the OAR in xml format
* `http://${API_ENDPOINT}/search?of=xm&jrec=1&rg=10`

  * Parameters:
    * `of` = output format (e.g. `xm` for MARCXML)
    * `jrec` = jump to record ID (e.g. 1 for first hit)
    * `rg` = records-in-groups-of (e.g. 10 hits per page)

#### Paginate results

By setting `**jrec**` and `**rg**` properly to paginate the output, as example:

* Get records from 1 to 10
    `http://${API_ENDPOINT}/search?of=xm&jrec=1&rg=10`
* Get records from 11 to 20:
  `http://${API_ENDPOINT}/search?of=xm&jrec=11&rg=10`
* Get records from 11 to 20:
  `http://${API_ENDPOINT}/search?of=xm&jrec=22&rg=10`


#### Look for pattern in fields

* Get the first 10 records that contains the string “Hackfest” in the title:
  `http://${API_ENDPOINT}/search?p=Hackfest&f=title&jrec=0&rg=10&of=xm`

* Get the first 10 records in **PRESENTATIONSNADRE** collection that contains **NADRE** in keyword:  `http://${API_ENDPOINT}/search?p1=collection:PRESENTATIONSNADRE+keyword:NADRE&of=xm&jrec=1&rg=10`

### <a name="jsonapi" />JSON API

In this section you will see the same examples saw above, but the output, this time, is in JSON format.

#### Get first 10 records in the OAR

The following is the query to get the first 10 in the OAR in xml format
* `http://${API_ENDPOINT}/search?of=recjson&jrec=1&rg=10`

  * Parameters:
    * `of` = output format (e.g. `xm` for MARCXML)
    * `jrec` = jump to record ID (e.g. 1 for first hit)
    * `rg` = records-in-groups-of (e.g. 10 hits per page)

#### Paginate results

By setting `**jrec**` and `**rg**` properly to paginate the output, as example:

* Get records from 1 to 10
    `http://${API_ENDPOINT}/search?of=recjson&jrec=1&rg=10`
* Get records from 11 to 20:
  `http://${API_ENDPOINT}/search?of=recjson&jrec=11&rg=10`
* Get records from 11 to 20:
  `http://${API_ENDPOINT}/search?of=recjson&jrec=22&rg=10`


#### Look for pattern in fields

* Get the first 10 records that contains the string “Hackfest” in the title:
  `http://${API_ENDPOINT}/search?p=Hackfest&f=title&jrec=0&rg=10&of=recjson`

* Get the first 10 records in **PRESENTATIONSNADRE** collection that contains **NADRE** in keyword:  `http://${API_ENDPOINT}/search?p1=collection:PRESENTATIONSNADRE+keyword:NADRE&of=recjson&jrec=1&rg=10`

For further information, see the [Search Engine API documentation](https://nadre.ethernet.edu.et/help/hacking/search-engine-api)
