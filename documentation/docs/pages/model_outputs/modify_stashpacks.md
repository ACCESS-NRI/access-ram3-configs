{% set model = "ACCESS-rAM3" %}
{% set ras_id = "u-bu503" %}
{% set rns_id = "u-by395" %}
{% set branch = "nci_access_ram3" %}
{% set mosrs_config_ras = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/7/trunk" %}
{% set mosrs_config_rns = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/8/trunk" %}
{% set model_configurations = "/models/access-ram" %}
{% set release_notes = "https://forum.access-hive.org.au/t/access-ram3-release-information/4308" %}

`stashpack 6` is a user-definable stashpack that has been populated to get you started.
 
After you [Customize non-optional STASH](/model_outputs/customize_stash), the **new** content can be moved/copied to `stashpack 6` using the following steps:

1) Find the ~/roses/<suite-id\>/app/um/rose-app.conf file

2) Isolate the **new** content that you would like to move to `stashpack 6`

3) Append the **new** content to the `~/roses/<suite-id\>/app/um/opt/rose-app-stashpack6.conf` file.

4) Delete the **new** content from the ` ~/roses/<suite-id\>/app/um/rose-app.conf` file.

!!! tip
    To isolate the **new** content in ~/roses/<suite-id\>/app/um/rose-app.conf, take a copy of the file before you edit it.

!!! warning
    Keep track of edits you make and what files need to be reverted to the original.

