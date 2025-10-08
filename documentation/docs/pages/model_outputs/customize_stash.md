{% set model = "ACCESS-rAM3" %}
{% set ras_id = "u-bu503" %}
{% set rns_id = "u-by395" %}
{% set branch = "nci_access_ram3" %}
{% set mosrs_config_ras = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/7/trunk" %}
{% set mosrs_config_rns = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/8/trunk" %}
{% set model_configurations = "/models/access-ram" %}
{% set release_notes = "https://forum.access-hive.org.au/t/access-ram3-release-information/4308" %}

### What does a STASH request involve?

STASH requests involve choosing:

| name | description |
|------|-------------|
|variable|You can select from variables defined in a STASHmaster file.  Variables are grouped in Sections and have a STASHcode associated with them|
|usage profile|Usage profiles are essentially links to output stream (*files*) that the data will be written to|
|domain profile|A spatial grid to write the data out on (may differ from the variable grid)|
|time profile|A selection of times with the time processing (i.e. instantaneous, maximum, minimum, average, etc)|

!!! tip
    If making a new STASH request for the first time, we recommend that you look at existing STASH requests similar to what you want and **cloning** or **copying** them.
    (This can be done by right clicking on the existing request and selecting **cloning** from the drop-down menu).

### add a new STASH request.

Navigate to:

_um &rarr; namelist &rarr; Model Input and Output &rarr; STASH Requests and Profiles &rarr; STASH requests_

!!! tip
    The link to *um* will be greyed out.  Click on the *um* link and it will load.

On the right side of the screen is a **New+** button, click on it.

A selection screen will appear with many sections outlined on it.  Click on a section (if you know what you want), then on the item you want. Use the **Filter** to search for your variable to narrow the search (at either stage). The click on the **Add+** button and close the screen. 
!!! Tip
    You can add multiple variables at the same time before closing the screen.


Back in _um &rarr; namelist &rarr; Model Input and Output &rarr; STASH Requests and Profiles &rarr; STASH requests_, the new requests will have red *X*'s in them because they need to be filled out.
Choose from a drop-down list the domain_profile, time_profile and usage_profile you want, then click "Save"


### add a new domain_profile, time_profile and usage_profile

#### To create a domain profile

Navigate to

_um &rarr; namelist &rarr; Model Input and Output &rarr; STASH Requests and Profiles &rarr; Domain Profiles_

Click on the **Add+** button.

Make the relevant selections.

#### To create a time profile 

_um &rarr; namelist &rarr; Model Input and Output &rarr; STASH Requests and Profiles &rarr;  Time Profiles_

Click on the **Add+** button.

Make the relevant selections.

#### To create a usage profile
Creating a new usage profile is more complex than creating a domain or time profile as it requires to two steps to have been completed.

##### 1) If necessary, create an output stream
If you want your usage profile to be associated with a new file, you need to create an Output Stream first by navigating to:
_um &rarr; namelist &rarr; Model Input and Output &rarr; Model Output Streams_

Click on the **Add+** button.

Make the relevant selections.

##### 2) Create a usage stream (linked to an output stream)
To then link it to a usage profile, navigate to:

_um &rarr; namelist &rarr; Model Input and Output &rarr; STASH Requests and Profiles &rarr;  Usage Profiles_

Click on the **Add+** button.

Make the relevant selections, ensuring to link it to the output stream you require (as identified by the name you configured beforehand or one that previously existed).

!!! warning
    Even if you have done everything write, the STASH request may produce no data.
    This is because some requests are not allowed with certain versions of the model.

Once you are happy with your new non-optional STASHpack, you can [add the contents to an optional stashpack](/model_outputs/modify_optional_stashpacks)
