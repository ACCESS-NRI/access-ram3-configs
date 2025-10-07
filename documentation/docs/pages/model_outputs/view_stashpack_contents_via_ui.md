{% set model = "ACCESS-rAM3" %}
{% set ras_id = "u-bu503" %}
{% set rns_id = "u-by395" %}
{% set branch = "nci_access_ram3" %}
{% set mosrs_config_ras = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/7/trunk" %}
{% set mosrs_config_rns = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/8/trunk" %}
{% set model_configurations = "/models/access-ram" %}
{% set release_notes = "https://forum.access-hive.org.au/t/access-ram3-release-information/4308" %}

To view `stashpack <N>`, where N = 1,2 ..., 7  you can:

1) Append `~/roses/<suite-id\>/app/um/opt/rose-app-stashpack<N>.conf` to the ~/roses/<suite-id\>/app/um/rose-app.conf file

2) View your selection via the Rose UI (for advice see [Customize STASH](/model_outputs/customize_stash))
   
- *Please note, that the original non-optional stashpack contents will be included in the Rose UI results as well.*

3) Remember to revert to the original version of ~/roses/<suite-id\>/app/um/rose-app.conf once you are finished. (Unless you intend to [modify the contents](/model_outputs/customize_stash) using the non-optional stashpack).

!!! tip
    To isolate the **new** content in ~/roses/<suite-id\>/app/um/rose-app.conf, take a copy of the file before you edit it.

