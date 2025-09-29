{% set model = "ACCESS-rAM3" %}
{% set ras_id = "u-bu503" %}
{% set rns_id = "u-by395" %}
{% set branch = "nci_access_ram3" %}
{% set mosrs_config_ras = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/7/trunk" %}
{% set mosrs_config_rns = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/8/trunk" %}
{% set model_configurations = "/models/access-ram" %}
{% set release_notes = "https://forum.access-hive.org.au/t/access-ram3-release-information/4308" %}

### NaNs in error term in BiCGstab

In some cases the choice of location and time produces initial conditions of the low resolution nest that leads to an unstable model state, causing a crash with an error similar to the following:

```
????????????????????????????????????????????????????????????????????????????????
???!!!???!!!???!!!???!!!???!!!       ERROR        ???!!!???!!!???!!!???!!!???!!!
?  Error code: 1
?  Error from routine: EG_BICGSTAB
?  Error message: NaNs in error term in BiCGstab after      1 iterations
?        This is a common point for the model to fail if it
?        has ingested or developed NaNs or infinities
?        elsewhere in the code.
?        See the following URL for more information:
?        https://code.metoffice.gov.uk/trac/um/wiki/KnownUMFailurePoints
?  Error from processor: 216
?  Error number: 22
????????????????????????????????????????????????????????????????????????????????
```

If that occurs, two possible work-arounds are:

- Reduce the GAL9 timestep from `300` to `150` seconds.<br>
  To achieve this, set `rg01_rs01_m01_dt` to `150` in the `rose-suite.conf` file.<br>
  This does not have a large impact on cycle time, and can usually be reverted in subsequent cycles when the simulation is running without error.
- Change the `INITIAL_CYCLE_POINT` in the `rose-suite.conf` file to an earlier day (usually 1 day should be enough).
  This can sometimes solve the issue, though at the expense of running the model simulation for longer than was initially desired.

More on this error in the [related forum post](https://forum.access-hive.org.au/t/issues-with-access-ram-ocean-domains-u-dg767-and-nans-in-bicgstab-u-dg768/4418).

