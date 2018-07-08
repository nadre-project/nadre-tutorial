# How to use the `php` examples.

This folder contains some examples on how to submit different kinds of assets on an Open Access repository based on invenio. In particular you can find examples for datasets, images etc...

The <object_type>-submission-to-OAR.php file contains a simple php script to submit the digital object to the OAR.
You can perform these examples running the scripts using `php` command. Is mandatory have `php-cli` installed and `php-curl` library. To install them on an Ubuntu based machine you can issue `apt-get install php5-cli php5-curl`.

## How to perform the examples
1. <a name="ref"></a> Export a variable with the repository endpoint `export API_ENDPOINT=invenio_endpoint`
1. Edit the `<object_type>-submission-to-OAR.xml` file in `xml` folder according with your requirements
1. Run the php script, using the invenio endpoint exported at [1](#ref). `php <object_type>-submission-to-OAR.php ${API_ENDPOINT}`. The should look like: `[INFO] bibupload batchupload --insert /opt/invenio/var/tmp-shared/batchupload_20180708091104_k4qsQk`
