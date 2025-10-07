{% set model = "ACCESS-rAM3" %}
{% set ras_id = "u-bu503" %}
{% set rns_id = "u-by395" %}
{% set branch = "nci_access_ram3" %}
{% set mosrs_config_ras = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/7/trunk" %}
{% set mosrs_config_rns = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/8/trunk" %}
{% set model_configurations = "/models/access-ram" %}
{% set release_notes = "https://forum.access-hive.org.au/t/access-ram3-release-information/4308" %}

To toggle a _stashpack_ within the [Rose GUI](#rosegui), navigate to 

_suite conf &rarr; Nesting Suite &rarr; Nested region 1 setup &rarr; Resolution 1 setup &rarr; Config 1 setup_. 

Toggle a specific _stashpack_ within the `rg01_rs01_m01_stashpack` field and click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.<br>

Similar steps can be repeated for the

_suite conf &rarr; Nesting Suite &rarr; Nested region 1 setup &rarr; Resolution 2 setup &rarr; Config 2 setup_ `rg01_rs02_m02_stashpack` field.<br>

So and so forth.

For example, to enable `stashpack 6` (that includes variables such as wind gust, mean sea level pressure and rainfall amount, for every model timestep) in all nests, set the `6th` button of both `rg01_rs01_m01_stashpack` and `rg01_rs02_m02_stashpack` fields to `true`.

