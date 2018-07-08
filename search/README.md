<!-- Copyright 2016 Sci-GaIA Consortium

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License. -->


# Programmatic interaction with an Invenio based Open Access Repository

This directory shows how to interact with the Invenio API to use the Open Access repository. Warmups are in the language-specific directories:

  * curl
  * php

## Search Engine

  * Syntax: `GET /search?p=...&of=...&ot=...&jrec=...&rg=...`
    _e.g._ http://${API_ENDPOINT}/search?p1=collection:PRESENTATIONSNADRE&of=recjson&jrec=1&rg=10

  * Parameters:
    * `p` = pattern (i.e. your query)
    * `of` = output format (e.g. `xm` for MARCXML)
    * `ot` = output tags (e.g. `''` to get all fields, `100` to get titles only)
    * `jrec` = jump to record ID (e.g. 1 for first hit)
    * `rg` = records-in-groups-of (e.g. 10 hits per page)

      _e.g._ http://${API_ENDPOINT}/search?p1=collection:PRESENTATIONSNADRE+keyword:NADRE&of=recjson&jrec=1&rg=10

  * Example: (returning full XML or JSON output)
      * XML output : http://${API_ENDPOINT}/search?p1=collection:PRESENTATIONSNADRE&of=xm
      * JSON output : http://${API_ENDPOINT}/search?p1=collection:PRESENTATIONSNADRE&of=recjson
      * Search (doi - title) :
        * Search with keywords http://${API_ENDPOINT}/search?p1=collection:PRESENTATIONSNADRE+author:Barbera+keyword:NADRE&of=recjson&ot=title,authors,doi&jrec=1&rg=10

For further information, see http://${API_ENDPOINT}/help/hacking/search-engine-api

## Submit
