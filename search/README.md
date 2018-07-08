# Search Engine applicable

Invenio has Search Engine API, you can use find what you are looking for, and then amend a few URL parameters to turn the query into an XML API one.

* Syntax: `GET /search?p=...&of=...&ot=...&jrec=...&rg=...`

To get the full list of available parameters you can have a look [here](https://nadre.ethernet.edu.et/help/hacking/search-engine-api).


## Examples

### XML API

#### Get first 10 records

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

* Get the first 10 records in given collection that contains a given keyword:  `http://${API_ENDPOINT}/search?p1=collection:**PRESENTATIONSNADRE+keyword:NADRE**&of=xm&jrec=1&rg=10`

For further information, see http://${API_ENDPOINT}/help/hacking/search-engine-api
