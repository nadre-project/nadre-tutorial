## COMMAND
curl -T ../xml/presentation-submission-to-OAR.xml http://${API_ENDPOINT}/batchuploader/robotupload/insert -A invenio_webupload -H "Content-Type: application/marcxml+xml"

## EXPECTED OUTPUT
[INFO] bibupload batchupload --insert /opt/invenio/var/tmp-shared/batchupload_20161122(...)
