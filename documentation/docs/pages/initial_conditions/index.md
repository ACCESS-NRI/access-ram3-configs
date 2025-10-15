The RNS gives options in terms of the driving model.  To see the options navigate to:

- _suite conf &rarr; Nesting Suite &rarr; Driving model setup_


On the Australian [Gadi](https://opus.nci.org.au/display/Help/0.+Welcome+to+Gadi#id-0.WelcometoGadi-Overview) Supercomputer, in research mode the most commonly used approach is to use 

- `dm_name` = ECMWF forecast fields and
- `dm_ec_mode` = EC analysis/re-analysis.

This is because researchers have access to the full ERA5 archive on NCI. 

The driving model provides initial and boundary conditions to the regional nesting suite.
Initial conditions are an instantaneous initial value from which the forecast starts.
Boundary conditions are values provided at the external bounds of the region nest, updated at chosen temporal intervals (not the model timestep).

Generally, the driving model provides the lateral boundary conditions for resolution 1, with resolution > 1 getting boundary conditions from another run in the same nest (if configured that way).

!!! tip
    The RNS is highly configurable.  Start from an example close to what you want or ask for a review from another experienced user after setting up a new experiment.
    It is important to pay attention to all the details.

In this section are information on:

* [nesting considerations](nesting_considerations)
* [how to use a higher-quality land/surface dataset](replace_land_surface)
* [how to use a higher-quality sea surface temperature and ice dataset.](replace_sst_seaice)
