{% set model = "ACCESS-rAM3" %}

# Housekeeping tips

{{model}} can produce prolific amounts of data.  You can choose the amount of data that you want to keep and store via the **housekeeping** settings.


### RAS

There are no housekeeping options for the RAS.

The RAS though can create a large amount of data.

Once you are sure you no longer need the data produced by the RAS you can run the command

`rose suite-clean`

to delete the data.

### OAS

There are also no housekeeping options for the OAS.

The OAS produces large **global** OSTIA ancillary files and keeps them in the user-defined `OSTIA_OUTPUT` directory.

We may in time introduce the ability to use `rose suite-clean`, but for the moment
to remove unnecesary global OSTIA ancillary files, navigate to the `OSTIA_OUTPUT` directory (on your filesystem) and remove the unwanted files.

### RNS

In terms of housekeeping, for the RNS, there are two concerns:

- ERA5 data and
- Working files.

#### ERA5 data

To use ECMWF reanalysis data (ERA5), the data is first converted to the correct format before being used in the suite.
This is done by setting 

_suite conf &rarr; Nesting Suite &rarr; Driving model setup &rarr; NCI_ERA5GRIB to **true**_

when running the suite.

The files are converted and stored in 

_suite conf &rarr; Nesting Suite &rarr; Driving model setup &rarr; dm_ec_ic_lbc_dir_

We may in time introduce the ability to use `rose suite-clean`, but for the moment to delete the files, navigate to the `dm_ec_ic_lbc_dir` directory (on your filesystem) and remove the unwanted files manually.


#### Working files

The RNS creates lots data of data in the working directory.
You can choose how much of that data to keep after each cycle by navigating to:

_suite conf &rarr; Nesting Suite &rarr; General run options &rarr; HK_RUN_

There are two options to toggle on and off.  One for deleting all files except STASH outputs, and one for deleting STASH outputs.

By default we have turned the first option on.  You may want to turn it off so you can view all the intermediate files in the forecasting process.

Once you are finished with the suite and want to remove all the data it created (in the working directory) you can use the

 `rose suite-clean`

command.
