{% set model = "ACCESS-rAM3" %}
{% set ras_id = "u-bu503" %}
{% set rns_id = "u-by395" %}
{% set branch = "nci_access_ram3" %}
{% set mosrs_config_ras = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/7/trunk" %}
{% set mosrs_config_rns = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/8/trunk" %}
{% set model_configurations = "/models/access-ram" %}
{% set release_notes = "https://forum.access-hive.org.au/t/access-ram3-release-information/4308" %}



### Edit {{ model }} configuration
!!! tip 
    Due to the presence of two distinct suites ([RAS](#ras) and [RNS](#rns)), specific modifications might be required in either one or both.<br>
    For each of the following possible modifications, the relevant suite that needs editing is listed as a bullet point.

This section describes how to modify the {{ model }} configuration.
    
The modifications discussed in this section can change the way the RAS and RNS are run, or how specific [model components] are configured and coupled together.

In general, ACCESS modelling suites can be edited either by directly modifying the configuration files within the suite directory, or by using the [_Rose_ GUI](#rosegui).
    
!!! warning
    Unless you are an experienced user, directly modifying configuration files is usually discouraged to avoid encountering errors.
    
##### Rose GUI {: #rosegui }
To open the [_Rose_](#rose) GUI, run the following command from within the [suite directory](#suitedir):
``` 
rose edit &
```
    
!!! tip 
    The `&` is optional. It allows the terminal prompt to remain active while running the `Rose` GUI as a separate process in the background.
        

#### Change the land-surface initial conditions source
- **RNS**<br>
    To change the [land-surface initial conditions source]({{ model_configurations }}/#land-surface-initial-conditions-source) within the [Rose GUI](#rosegui), navigate to _suite conf &rarr; Nesting Suite &rarr; Driving model setup_. Edit the `NCI_HRES_ECCB` field and click the _Save_ button ![Save button](/assets/run_access_cm/save_button.png){: style="height:1em"}.

    For example, to get the land-surface initial conditions from the `BARRA-R2` dataset, set the `NCI_HRES_ECCB` field to `BARRA2-R`.

!!! warning
    When changing the land-surface initial conditions source, it is important to ensure that the configuration of the nested region aligns with the [nest configuration requirements](#nest-configuration-requirements).

#### Change the simulation region
In {{ model }}, users can perform simulations for a particular region of the Earth by configuring specific parameters for each domain of interest (referred to as _nested region_).<br>

In {{ model }}, the following parameters are supported to configure the nested regions:

- [Nested region name](#change-the-nested-region-name)
- [Nested region position](#change-the-nested-region-position)
- [Nested region's nest configuration](#change-the-nested-regions-nest-configuration)

!!! warning
    Domain-specific changes need to be consistent between RAS and RNS. Therefore, for each of the configuration parameters listed above, consistent changes to both RAS and RNS will be required.

##### Change the nested region name {: .no-toc }
- **RAS**<br>
    To change a nested region name within the [Rose GUI](#rosegui), navigate to _suite conf &rarr; Regional Ancillary Suite &rarr; Nested region 1 setup_. Edit the `rg01_name` field and click the _Save_ button ![Save button](/assets/run_access_cm/save_button.png){: style="height:1em"}.

    For example, to set the name of the nested region to `Darwin`, set the `rg01_name` field to `Darwin`.

- **RNS**<br>
    Changing the RAS nested region name changes the [RAS output path](#ras-output-files). As a consequence, the following changes are required within the RNS:

    - **Ancillary directory**<br>
        To change the first nest ancillary directory within the [Rose GUI](#rosegui), navigate to _suite conf &rarr; Nesting Suite &rarr; Nested region 1 setup &rarr; Resolution 1 setup_. Change the `rg01_rs01_ancil_dir` field by replacing `Lismore` with the chosen RAS nested region name, and click the _Save_ button ![Save button](/assets/run_access_cm/save_button.png){: style="height:1em"}.<br>
        The same step needs to be repeated for:

        - _suite conf &rarr; Nesting Suite &rarr; Nested region 1 setup &rarr; Resolution 2 setup_ `rg01_rs02_ancil_dir` field
        - _suite conf &rarr; Nesting Suite &rarr; Driving model setup_ `dm_ec_lam_ancil_dir` field

        For example, if the RAS nested region name was set to `Darwin`, replace `Lismore` in the `rg01_rs01_ancil_dir`, `rg01_rs02_ancil_dir` and `dm_ec_lam_ancil_dir` fields with `Darwin`.

    - **RNS nested region name**<br>
        To change the nested region name within the [Rose GUI](#rosegui), navigate to _suite conf &rarr; Nesting Suite &rarr; Nested region 1 setup_. Edit the `rg01_name` field and click the _Save_ button ![Save button](/assets/run_access_cm/save_button.png){: style="height:1em"}.

        For example, to set the name of the nested region to `Darwin`, set the `rg01_name` field to `Darwin`.

        !!! tip
            Changing the RNS nested region name is not strictly necessary, but it affects the [RNS outputs path](#rns-output-files). Therefore, for consistency, it is strongly recommended for RAS and RNS to have the same nested region names.

##### Change the nested region position {: .no-toc }
The nested region position is usually defined by the latitude and longitude coordinates of the nested region centre.

- **RAS**<br>
    To change the nested region centre within the [Rose GUI](#rosegui), navigate to _suite conf &rarr; Regional Ancillary Suite &rarr; Nested region 1 setup_. Edit the `rg01_centre` field and click the _Save_ button ![Save button](/assets/run_access_cm/save_button.png){: style="height:1em"}.

    For example, to set the centre of the nested region to `-12.4` / `130.8`, set the `rg01_centre` field to `-12.4` / `130.8`.

!!! warning
    When changing the land-surface initial conditions source, it is important to ensure that the configuration of the nested region aligns with the [nest configuration requirements](#nest-configuration-requirements).

##### Change the nested region's nest configuration {: .no-toc }
Each nested region can contain multiple [nests]({{model_configurations}}/#nesting) (referred to as _Resolutions_ within the RAS and RNS), each of them being a separate domain where the simulation experiment is carried out.<br>
Typically, nests within the same nested region are arranged concentrically, with increasingly smaller dimensions and higher resolutions towards the innermost nests.

<div markdown id='nest-configuration-requirements'>
!!! warning
    Currently, {{model}} only supports specific nest configurations that meet the following criteria:

    The grid points of the RAS first inner nest (i.e., _Resolution 2_, because _Resolution 1_ always corresponds to the outer ERA5 domain) must align with those of the [land-surface initial conditions dataset]({{model_configurations}}/#land-surface-initial-conditions-source). Thus, the configuration of the RAS first inner nest (_Resolution 2_), including its position, dimension and resolution, need to be modified accordingly. Note that the position of a nest is also influenced by the [nested region position](#change-the-nested-region-position).
</div>

