## Sample xml file

This folder contains the xml files used to describe the digital object you're going to upload.
You can refer to them in the curl and php submission examples.

Before to actually proceed with object submission you have to replace the `<subfield code="a">` value, in `<datafield ag="024" ...`, with the reserved DOI for the asset. To generate a test DOI you can issue:
```
 python request_doi.py
```
This script will return a test that you can put in the xml file.
