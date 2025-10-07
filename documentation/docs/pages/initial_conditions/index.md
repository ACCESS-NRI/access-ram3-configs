# Driving model

## Overview
The RNS gives options in terms of the driving model.  To see the options navigate to:

- _suite conf &rarr; Nesting Suite &rarr; Driving model setup_


On the Australian [Gadi](https://opus.nci.org.au/display/Help/0.+Welcome+to+Gadi#id-0.WelcometoGadi-Overview) Supercomputer, in research mode the most commonly used approach is to use 

- `dm_name` = ECMWF forecast fields and
- `dm_ec_mode` = EC analysis/re-analysis.

This is because researchers have access to the full ERA5 archive on NCI. 

The driving model provides initial and boundary conditions to the regional nesting suite.
Initial conditions are an instantaneous initial value from which the forecast starts.
Boundary conditions are values perovided at the external bounds of the region nest, updated at chosen temporal intervals (not the model timestep).

Generally, the driving model provides the lateral boundary conditions for resolution 1, with resolution > 1 getting boundary conditions from another run in the same nest (if configured that way).

!!! tip
    The RNS is highly configurable.  Start from an example close to what you want or ask for a review from another experienced user after setting up a new experiment.
    It is important to pay attention to all the details.


## Reconfiguration 

When driving model is not available at the resolution of the target nest/resolution 1 the driving model is "reconfigured" onto the target nest/resolution 1.
See the resolution (in degrees) of commonly used input datasets below.

|dataset|resolution|
|-------|----------|
|ERA5|0.25°|
|BARRA-R2| 0.11°|
|ERA5-land|0.1°|
|OSTIA|0.05°|


Hence, choices in the driving model dataset affect [nesting choices](/configurations) settings.

A pre-filled example based on ERA5 driving model with a 2.2km has been constructed with a double-level nest to enhance the accuracy of the run (by allowing the forecast model to "fill-in" some of missing details).

This has been down to allow for other higher quality reference datasets to be used to "replace" some of the driving model initial conditions.  Hence, the double-nest allowed the opportunity to offer users to ability to use higher quality [land/surface](/initial_conditions/initial_conditions_land_surface).
Higher quality [sea-surface temperature and sea-ice](/initial_conditions/initial_conditions_sst_seaice) conditions can also be utilized.
