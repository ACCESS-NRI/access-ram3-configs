# Replace land/surface

The following **replacement** higher-quality land/surface datasets exist and can be used in place of the driving model land/surface values in the RNS :

|dataset|resolution|
|-------|----------|
|BARRA-R2| 0.11°|
|ERA5-land|0.1°|

!!! warning
    If using the higher-quality `BARRA-R2` or `ERA5-land` dataset you must ensure that the [central position](/configurations/modify-nest#change-the-central-position-of-the-entire-nest) of the nest is chosen from within that dataset AND that `nest 1/resolution 1` has the same resolution as the chosen dataset. Otherwise, if using 'None' the land/surface are not being replace and the central position of `nest 1/resolution 1` is unrestricted.  

## Update the RAS 

If needed, [change the RAS](/configurations/modify-nest#modify-the-ras) to have a [central position](/configurations/modify-nest#change-the-central-position-of-the-entire-nest) selected from the chosen reference dataset.

Ensure that the resolution of `nest 1 / resolution 1` (and `nest 1 / resolution 2` if using ERA5 driving conditions) is the same as the resolution of the chosen reference dataset (see the table above).

## Update the RNS

Next, [modify the RNS](/configurations/modify-nest#modify-the-rns)

### Change the land-surface initial conditions source

To change the land-surface initial conditions source within the Rose GUI, navigate to 

_suite conf &rarr; Nesting Suite &rarr; Driving model setup_.

Edit the `NCI_HRES_ECCB` field and click the _Save_ button ![Save button](/assets/save_button.png){: style="height:1em"}.

For example, to get the land-surface initial conditions from the `BARRA-R2` dataset, set the `NCI_HRES_ECCB` field to `BARRA2-R`.

(action - link to papers describing the data sources)
