# Rose/cylc suite overview

Before we get started, lets define the acronyms used in this section:

|Acronym|Definition|
|-------|----------|
|RAS| Regional Ancillary Suite|
|RNS| Regional Nesting Suite|
|OSTIA| Operational Sea Surface Temperature and Sea Ice Analysis (OSTIA) system|
|OAS| OSTIA Ancillary Suite|

Running a regional model has a cost in terms of [SUs](https://opus.nci.org.au/spaces/Help/pages/236880942/Job+Costs...) and storage.  To reduce the cost of running a regional model, tasks that only need to be run once are handled separately to those that are run constantly.  The RAS handles the tasks that only need to be run once and the RNS handles the tasks that are constantly varying.   The key difference between the RAS and RNS is that the RAS is date-agnostic, whereas the RNS handles datasets that are date/time specific.
<br><br>
The RAS settings define the target grid files created used by both the RAS and RNS. Target grids definitions are required to regrid and subset other datasets onto the latitudes and longitudes designated in the RAS (target grid file) settings.  For example, reference datasets orography sit on disk at a native resolution, globally.  The RAS cuts-out and regrids the native orography dataset onto the target grid and leaves them in a file on disk that the RNS can later read in.  The RAS does this for all datasets that are either held static for modelling purposes or monthly-varying.
<br><br>
The RNS settings define the date/times for the run, driving model, physics, output and other choices.  The RNS uses the target grid definition created by the RAS to regrid driving model data (initial conditions and lateral boundary conditions) <b>for the date/times selected</b>.  Therefore the target grid definition created by the RAS needs to be updated in the RNS each time it changes.  Note, there is a separate target grid definition for each nest of the RNS.
!!! tip
    The selection of driving model affects the number of target grids required. i.e. If ERA5 is selected as the driving model in the RNS an additional target grid needs to be defined in the RAS (for the purpose of cutting out and regridding ERA5 data).
        {: style="list-style-type: disc"}

The RNS has a USE_OSTIA option that causes SST and sea-ice values to be updated at the start of the run, then every 06Z afterwards with OSTIA data.  The OSTIA data is expected to be stored in files pre-prepared using the OAS.  The OAS is an optional suite used to transform OSTIA data sitting on disk (in netcdf format) to the format expected by the RNS, if you choose to use it.  The OAS output directory must match the RNS OSTIA directory.  OSTIA data changes day-to-day with a separate file per date.

