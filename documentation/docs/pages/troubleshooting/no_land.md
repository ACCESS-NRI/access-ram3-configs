{% set model = "ACCESS-rAM3" %}
{% set ras_id = "u-bu503" %}
{% set rns_id = "u-by395" %}
{% set branch = "nci_access_ram3" %}
{% set mosrs_config_ras = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/7/trunk" %}
{% set mosrs_config_rns = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/8/trunk" %}
{% set model_configurations = "/models/access-ram" %}
{% set release_notes = "https://forum.access-hive.org.au/t/access-ram3-release-information/4308" %}

### No-land and isolated land experiments
Configuring an experiment that contains only ocean points for the inner nests, with no land at all, is not supported by the UM.
In some cases, even when small groups of isolated land points are present there is not data available for those land points in the forcing datasets.<br>
This can cause issues in the RAS suite similar to the following:

```
Calculating bi-linear interpolation coeffs
Finding coastal points
Setting coastal values
 WARNING - No source data is available in target domain
UNRESOLVED GRID POINTS IN SOIL DATASET
 Number of points unresolved is                      9
 POINT      78674 LAT   -29.0100 LONG   167.9304
 POINT      78675 LAT   -29.0100 LONG   167.9502
 POINT      79124 LAT   -29.0298 LONG   167.9304
 POINT      79125 LAT   -29.0298 LONG   167.9502
 POINT      79126 LAT   -29.0298 LONG   167.9700
 POINT      79127 LAT   -29.0298 LONG   167.9898
 POINT      79574 LAT   -29.0496 LONG   167.9304
 POINT      79575 LAT   -29.0496 LONG   167.9502
 POINT      79576 LAT   -29.0496 LONG   167.9700
 Search radius                      1
 NO DATA FROM WHICH TO SET UNRESOLVED POINTS
 ***ERROR: No source data available in target domain
```

The only work-around in this case is to choose a different domain such that the inner nest contains more land points.

More on this error in the [related forum post](https://forum.access-hive.org.au/t/issues-with-access-ram-ocean-domains-u-dg767-and-nans-in-bicgstab-u-dg768/4418).

