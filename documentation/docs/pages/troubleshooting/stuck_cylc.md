{% set model = "ACCESS-rAM3" %}
{% set ras_id = "u-bu503" %}
{% set rns_id = "u-by395" %}
{% set branch = "nci_access_ram3" %}
{% set mosrs_config_ras = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/7/trunk" %}
{% set mosrs_config_rns = "https://code.metoffice.gov.uk/trac/roses-u/browser/d/g/7/6/8/trunk" %}
{% set model_configurations = "/models/access-ram" %}
{% set release_notes = "https://forum.access-hive.org.au/t/access-ram3-release-information/4308" %}

### Stuck cylc tasks
Testing of the RAS revealed an intermittent problem: sometimes tasks in `{{ ras_id }}` remain stuck in a _submitted_ state within the _Cylc_ GUI. 
Using `qstat` revealed that they had failed, but this was not correctly reflected in the GUI.

To test this error, run:

```
cat ~/cylc-run/{{ ras_id }}/log/job/1/<task_name>/01/job.err
```

and you should get an output similar to the following:

```
/local/spool/pbs/mom_priv/jobs/140074859.gadi-pbs.SC: line 104: /g/data/hr22/apps/cylc7/cylc_7.9.9/lib/cylc/job.sh: No such file or directory
/local/spool/pbs/mom_priv/jobs/140074859.gadi-pbs.SC: line 105: cylc__job__main: command not found
```

The workaround for this is to use the _Cylc_ GUI to:

1. Set the task state to failed.
2. Set the task state to waiting.
3. Check that the task then automatically goes into submitted, then running, then succeeded.

This is an intermittent, and often unreproducible error, hence the task should succeed when resubmitted. This issue has been reported to NCI.
