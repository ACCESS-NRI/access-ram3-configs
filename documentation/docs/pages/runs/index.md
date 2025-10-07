# Testing versus production runs

| Name | Description|
|------|------------|
|Production| The full publication-level run|
|Testing| A initial run through of all the model settings to search for **bugs**|

Production runs can be enormously expensive.  In addition, it is completely normal for users to make simple errors when changing set-ups.  Especially when change the location and size of the region/resolutions.

ACCESS-NRI is advocating for users to get comfortable with the concept of testing and production runs.

Testing runs are short and cheap and designed solely to check whether paths are correct, executables can be found storage flags are set correctly, etc.

By running shorter runs you will save time and computing resources.


To convert you production run into a test run you can change the chunk length `CRUN_LEN` and length of a full cycle `CYCLE_INT_HR` to 1.

To do so, change to the RNS directory.

`rose edit`

Navigate to:

_suite conf &rarr; Nesting Suite &rarr; General run options_.

_set `CRUN_LEN` to 1._

Click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.

Then navigate to:

_suite conf &rarr; Nesting Suite &rarr; Cycling options_.

_set `CYCLE_INT_HR` to 1._

Click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.

Modify all your settings and run this shortened verion of your suite until you are happy with the settings, then move on to the full-production level run.


