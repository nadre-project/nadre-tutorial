# Search Engine API

Invenio has a Search Engine API, you can use to find what you are looking for. It basically allows you to search for records in the repository, simply creating HTML quey string, like:

* Syntax: `GET /search?p=...&of=...&ot=...&jrec=...&rg=...`

To get the full list of available parameters you can have a look at the [Search Engine API documentation](https://nadre.ethernet.edu.et/help/hacking/search-engine-api).

## Examples

Invenio provides three different kinds of API

1. XML API
2. JSON API
3. Pyhton API

In the following sections you will see [XML API](#xmlapi) and then [JSON API](#jsonapi). You can use these examples by coping the URL in your browser. Otherwise you can can use the [curl](http://www.mit.edu/afs.new/sipb/user/ssen/src/curl-7.11.1/docs/curl.html) command line tool. In this tutorial I show you how to perform them in a browser.

### <a name="xmlapi" />XML API

Using these APIs will return results in XML format.

#### Get first 10 records in the OAR

The following is the query to get the first 10 in the OAR in xml format
<a href="http://nadre.ethernet.edu.et/search?of=xm&jrec=1&rg=10" target="_blank">http://nadre.ethernet.edu.et/search?of=xm&jrec=1&rg=10</a>

  * Parameters:
    * `of` = output format (e.g. `xm` for [MARCXML](http://nadre.ethernet.edu.et/help/admin/howto-marc))
    * `jrec` = jump to record ID (e.g. 1 for first hit)
    * `rg` = records in groups of (e.g. 10 hits per page)

#### Paginate results

By setting **jrec** and **rg** properly to paginate the output, as example:

* Get records from 1 to 10
  `http://nadre.ethernet.edu.et/search?of=xm&jrec=1&rg=10`
* Get records from 11 to 20:
  `http://nadre.ethernet.edu.et/search?of=xm&jrec=11&rg=10`
* Get records from 21 to 30:
  `http://nadre.ethernet.edu.et/search?of=xm&jrec=21&rg=10`

> Do not set **rg** too high, there is a server-wide safety limit for it.

#### Look for pattern in fields

* Get the first 10 records that contains the string '**Hackfest**' in the title:
  `http://nadre.ethernet.edu.et/search?p=Hackfest&f=title&jrec=0&rg=10&of=xm`

* Get the first 10 records in '**PRESENTATIONSNADRE**' collection that contains '**NADRE**' in keyword:  `http://nadre.ethernet.edu.et/search?p1=collection:PRESENTATIONSNADRE+keyword:NADRE&of=xm&jrec=1&rg=10`

#### Filter records and outputs in OAR

##### Filter records
* Get all records uploaded from a given date (e.g. 2018-01-01) to another given date (e.g. 2018-02-22)
  `http://nadre.ethernet.edu.et/search?of=xm&d1=2018-01-01&d2=2018-02-22`

Where:
  * **d1**: is the first date in `YYYY-mm-dd` format
  * **d2**: is the second date in `YYYY-mm-dd` format

### <a name="jsonapi" />JSON API

In this section you will see the same examples saw above, but the output, this time, is in JSON format. To get ouput in JSON format sets: `of=recjson`.
To better understand the output returned by the OAR I installed a plugin in my browser that  that makes the JSON results human readable.

#### Get first 10 records in the OAR

The following is the query to get the first 10 in the OAR in xml format
  ```bash
  curl 'http://nadre.ethernet.edu.et/search?of=recjson&jrec=1&rg=10' | jq .
  ```

  * Parameters:
    * `of` = output format (e.g. `xm` for MARCXML)
    * `jrec` = jump to record ID (e.g. 1 for first hit)
    * `rg` = records in groups-of (e.g. 10 hits per page)

#### Paginate results

By setting **jrec** and **rg** properly to paginate the output, as example:

* Get records from 1 to 10
  ```bash
  curl 'http://nadre.ethernet.edu.et/search?of=recjson&jrec=1&rg=10' | jq .
  ```
* Get records from 11 to 20:
  ```bash
  curl 'http://nadre.ethernet.edu.et/search?of=recjson&jrec=11&rg=10' | jq .
  ```
* Get records from 21 to 30:
  ```bash
  curl 'http://nadre.ethernet.edu.et/search?of=recjson&jrec=21&rg=10' | jq .
  ```

> Do not set **rg** too high, there is a server-wide safety limit for it.

#### Look for pattern in fields

* Get the first 10 records that contains the string “Hackfest” in the title:
  ```bash
  curl 'http://nadre.ethernet.edu.et/search?p=Hackfest&f=title&jrec=0&rg=10&of=recjson' | jq .
  ```

* Get the first 10 records in **PRESENTATIONSNADRE** collection that contains **NADRE** in keyword:  
  ```bash
  curl 'http://nadre.ethernet.edu.et/search?p1=collection:PRESENTATIONSNADRE+keyword:NADRE&of=recjson&jrec=1&rg=10' | jq .
  ```

#### Filter records and outputs in OAR

##### Filter records
* Get all records uploaded from a given date (e.g. 2018-01-01) to another given date (e.g. 2018-02-22)
  ```bash
  curl 'http://nadre.ethernet.edu.et/search?of=recjson&d1=2018-01-01&d2=2018-02-22' | jq .
  ```

Where:
  * **d1**: is the first date in `YYYY-mm-dd` format
  * **d2**: is the second date in `YYYY-mm-dd` format

##### Filter outputs
* Get only the **abstract**, **title** and authors of **resources**
  ```bash
  curl 'http://nadre.ethernet.edu.et/search?of=recjson&ot=abstract,title,authors' | jq .
  ```

Where:
  * **ot**: output tags, that is a comma separated lists of tags should be outputted (e.g. ‘’ to get all fields, ‘title’ to get titles only)

For further information, see the [Search Engine API documentation](https://nadre.ethernet.edu.et/help/hacking/search-engine-api)
