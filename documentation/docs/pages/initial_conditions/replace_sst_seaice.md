# Replace SST/sea-ice

The following **replacement** higher-quality sea surface temperature and sea ice dataset exist and can be used in place of the driving model values in the RNS:

|dataset|resolution|
|-------|----------|
|OSTIA|0.05°|

The RNS trunk has the ability to use global OSTIA ancillary files to replace SST and sea-ice values in the forecast both at the start of the run daily at 06Z.

There is an archive of global OSTIA ancillary files at the Met Office.  Instead of mirroring the Met Office global OSTIA ancillary archive ACCESS-NRI with NCI has made the full native OSTIA archive
available to Australian researchers.

A rose/cylc suite has been developed to transform the OSTIA data from its native netCDF format to the required UM ancillary file format for use in the RNS.

To **replace** SST and sea-ice with OSTIA values there are two steps required:

1) [modify the OSTIA ancillary suite (OAS)](#modify-the-oas) for the dates required.

2) [modify the RNS](#modify-the-rns) to use the OSTIA files including providing the path to them. 


### Get the OAS

To get the suite,   _rosie checkout **u-dk517**_


### Modify the OAS

OSTIA data is required for each day of the run in your experiment (plus sometimes the day prior, depending on start/end times).

Navigate to _suite conf &rarr; Ostia ancillary Generation Suite &rarr; Cycling options_

Modify the `INITIAL_CYCLE_POINT`

Modify the `FINAL_CYCLE_POINT`

Modify the `OSTIA_OUTPUT` directory

Then, _rose suite-run_


### Modify the RNS

#### Update the OSTIA settings

To change the land-surface initial conditions source within the Rose GUI for the **RNS**, navigate to 

_suite conf &rarr; Nesting Suite &rarr; Cycling options_.

Set `USE_OSTIA` to `True` and update `global_ostia_dir` to match the OAS `OSTIA_OUTPUT` directory.

!!! tip
    If OSTIA ancillaries are being kept in a project other than the one used to run the RNS, add the directory to NCI_STORAGE.

    i.e. if you are using files kept on vk83, but not running the RNS on project vk83, navigate to:

    <br>_suite conf &rarr; Nesting Suite &rarr; General options_

    <br> then add `+gdata/vk83` to `NCI_STORAGE`.
    

