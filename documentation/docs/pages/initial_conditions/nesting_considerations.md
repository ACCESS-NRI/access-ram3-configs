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
