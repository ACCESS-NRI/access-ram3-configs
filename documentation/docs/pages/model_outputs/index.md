# Model outputs

UM outputs are usually requested as a list of Spatial and Temporal Averaging and Storage Handling ([STASH](https://code.metoffice.gov.uk/doc/um/latest/papers/umdp_C04.pdf)) variables.<br>

There is a mandatory STASH (run for every nest/resolution) and STASHpacks that can be selected in each individual nest/resolution (currently 7).  

!!! tip
    STASHpack6 is the nominated `user-defined` STASHpack.


Given the complexity and differing levels of user experience, operations on the mandatory STASH output and the optional STASHpacks are described in separate sections (linked below).

| Name| Description|
|-----|------------|
|[Toggle STASHpacks](toggle_stashpacks)| pre-set grouping of data to be written out, easily switched on and off for separate combinations of nest and resolution.|
|[View STASHpack contents via the UI](view_stashpack_contents_via_ui)| View the contents of an optional STASHpack via the Rose User Interface|
|[Customize the mandatory STASH](customize_stash)| Customize the output being written (via the Rose User Interface)|
|[Modify STASHpacks](modify_stashpacks)| Modify the list of variables to be written out in optional STASHpack.|
|[Extend STASH](extend_stash)| Creating new STASH variables.|

!!! Warning
    STASH is very sophisticated and caters for many different model configurations.  A trade-off for the complexity is that sometime STASH configurations can be tricky to set up.
    Have patience or stick to pre-defined STASHpacks!


