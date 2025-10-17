# Change the date/time of the run.


### Update the OAS (if using)

Change into the OAS roses directory

When changing dates/times of a model run you need to ensure that OSTIA ancillary file available for the new time period.
To create new OSTIA ancillary files, please follow the [modify the OSTIA Ancillary Suite (OAS)](/initial_conditions/initial_conditions_sst_seaice)
ensure that the date/time period covers the target RNS run period.

`rose suite-run`


### Update the RNS

Change into the RNS roses directory

Navigate to suite conf → Nesting Suite → General run options

Modify the INITIAL_CYCLE_POINT

Modify the FINAL_CYCLE_POINT

`rose suite-run`

