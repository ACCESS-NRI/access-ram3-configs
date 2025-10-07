{% set model = "ACCESS-rAM3" %}
{% set ras_id = "u-bu503" %}
{% set rns_id = "u-by395" %}
{% set branch = "nci_access_ram3" %}
{% set mosrs_config_ras = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/7/trunk" %}
{% set mosrs_config_rns = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/8/trunk" %}
{% set model_configurations = "/models/access-ram" %}
{% set release_notes = "https://forum.access-hive.org.au/t/access-ram3-release-information/4308" %}

The terminology use below is described in the table below:

|term|description|
|----|-----------|
|nest| a collection of resolutions|
|resolution| a rectangular region covered by a specific number of grid points (a.k.a. resolution)

Please note that a single nest, can have multiple resolutions.  While a given resolution can provide initial conditions and lateral boundary 
conditions for the **next** resolution this is not always the case.  Pay attention to the details. 

!!! warning
    The numbering of the resolutions can differ between the  [RAS](/configurations/overview#ras) and [RNS](/configurations/overview#rns) (particularly if using EC as a driving model).
!!! tip
    Both the RAS and RNS can create multiple nests at the same time.  This capability should only be used by advanced users.
    Hence, we typically talk about **nest 1**.


To modify the location and/or the size of the target grids you need to modify both the ([RAS](/configurations/overview#ras) and [RNS](/configurations/overview#rns)).  This is because name changes in the RAS will affect the names and paths required in the RNS.

Modifications to the nest are done in the two (ordered) steps:

1) [modify the RAS](#modify-the-ras) and run the RAS.

2) [modify the RNS](#modify-the-rns) and run the RNS.

For further information, see below.


## Modify the RAS

To open the rose GUI, run the following command from within the RAS suite directory:
``` 
rose edit &
```

### Change the name of the entire nest {: .no-toc }
To change a nested region name within the rose GUI, navigate to

 _suite conf &rarr; Regional Ancillary Suite &rarr; Nested region 1 setup_. 

Edit the `rg01_name` field and click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.

For example, to change the  the name of the nested region from `Lismore` to `Darwin`, set the `rg01_name` field to `Darwin`.

### Change the central position of the entire nest {: .no-toc }
The nested region position is usually defined by the latitude and longitude coordinates of the nested region centre.

To change the nested region centre within the rose GUI, navigate to _suite conf &rarr; Regional Ancillary Suite &rarr; Nested region 1 setup_. Edit the `rg01_centre` field and click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.

For example, to set the centre of the nested region to `-12.4` / `130.8`, set the `rg01_centre` field to `-12.4` / `130.8`.

!!! warning
    When changing the land-surface initial conditions source, if using a [higher-quality land/surface initial condition](/initial_conditions/initial_conditions_land_surface) it is important to ensure that the centre of the nested region coincides with a pixel from that dataset.

### Change the number of resolution definitions contained within the entire nest {: .no-toc }
To change the number of resolution definitions for the nest within the rose GUI, navigate to _suite conf &rarr; Regional Ancillary Suite &rarr; Nested region 1 setup_. Edit the `rg01_nreslns` field and click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.


### Change the name of each individual "resolution" within the over-arching nest {: .no-toc }

The settings for each resolution nest within a nested region is defined separately.

For nest 1, resolution n, navigate to:

 _suite conf &rarr; Regional Ancillary Suite &rarr; Nested region 1 setup &rarr; Resolution n setup_ 

Here you can modify the "resolution" name, horizontal grid-length, number of points, offset and other settings.

For example, to set nest 1, resolution 2 name from  `d1100` to `d1000`, set the `rg01_rs02_name` field to `d1000`.



## Modify the RNS
!!! warning
    Domain-specific changes need to be consistent between RAS and RNS. For each of the configuration parameters listed above, consistently changes the RNS to match the RAS

Changing the RAS nested region name changes where the RAS output files are stored.

### Change the nested region name {: .no-toc }
To change the nested region name within the [Rose GUI](#rosegui), navigate to 

_suite conf &rarr; Nesting Suite &rarr; Nested region 1 setup_. 

Edit the `rg01_name` field and click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.

For example, to set the name of the nested region to `Darwin`, set the `rg01_name` field to `Darwin`.


### Change the name of each individual "resolution" within the over-arching nest 1 {: .no-toc }

To change the nest 1, resolution 1 name within the [Rose GUI](#rosegui), navigate to 

_suite conf &rarr; Nesting Suite &rarr; Nested region 1 setup &rarr; Resolution 2 setup _. 

Edit the `rg01_rs01_name` field and click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.

For example, to set the resolution name from  `d1100` to `d1000`, set the `rg01_rs01_name` field to `d1000`.



### Lastly, update the following ancillary directories {: .no-toc }

If you have changed the nested region name or the nested resolution names in the RAS, you need to update the ancillary directory names in each of the nest regions and the driving model if using ERA5 as a driving model.  For example, if the RAS nested region name was set to `Darwin`, replace `Lismore` and/or the RAS nest 1, resolution 1 name was set to `d1000`, then update the following paths to where the data now sits in the RAS.

- _suite conf &rarr; Nesting Suite &rarr; Nested region 1 setup &rarr; Resolution 1 setup_ `rg01_rs01_ancil_dir` field
- _suite conf &rarr; Nesting Suite &rarr; Nested region 1 setup &rarr; Resolution 2 setup_ `rg01_rs02_ancil_dir` field
- _suite conf &rarr; Nesting Suite &rarr; Driving model setup_ `dm_ec_lam_ancil_dir` field (if using ERA5 as a driving model)

Remember to click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.<br>

!!! tip
    Changing the RNS nested region name is not strictly necessary, but it affects the naming of the RNS output directories. Therefore, for consistency, it is strongly recommended for RAS and RNS to have the same nested region names.
    However, the ancil directory paths must be correct.


