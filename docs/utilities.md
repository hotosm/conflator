# Utility Programs

To conflate external datasets with OSM, the external data needs to be
converted to the OSM tagging schema. Otherwise comparing tags gets
very convoluted. Since every dataset uses a different schema, included
are a few utility programs for converting external datasets. Currently
the only datatsets are for highways. These datasets are available from
the [USDA](https://www.usda.gov/), and have an appropriate license to
use with OpenStreetMap. Indeed, some of this data has already been
imported. The files are available from the 
[FSGeodata Clearinghouse](https://data.fs.usda.gov/geodata/edw/datasets.php?dsetCategory=transportation)

Most of the fields in the dataset aren't needed for OSM, only the
reference number if it has one, and the name. Most of these highways
are already in OSM, but it's a bit of a mess, and mostly
unvalidated. Most of the problems are related to the TIGER import
in 2007. So the goal of these utilities is to add in the [TIGER
fixup](https://wiki.openstreetmap.org/wiki/TIGER_fixup) work by
updating or adding the name and a reference number. These utilities
prepare the dataset for conflation.

There are other fields in the datasets we might want, like surface
type, is it 4wd only, etc... but often the OSM data is more up to
date. And to really get that right, you need to ground truth it.

## mvum.py

This converts the [Motor Vehicle Use Map(MVUM)](https://data.fs.usda.gov/geodata/edw/edw_resources/shp/S_USA.Road_MVUM.zip) dataset that contains
data on highways more suitable for offroad vehicles. Some require
specialized offroad vehicles like a UTV or ATV. The data in OSM for
these roads is really poor. Often the reference number is wrong, or
lacks the suffix. We assume the USDA data is correct when it comes to
name and reference number, and this will get handled later by
conflation.

## roadcore.py

This converts the [Road Core](https://data.fs.usda.gov/geodata/edw/edw_resources/shp/S_USA.RoadCore_FS.zip) vehicle map. This contains data on all
highways in a national forest. It's similar to the MVUM dataset.

## Trails.py

This converts the [NPSPublish](https://data.fs.usda.gov/geodata/edw/edw_resources/shp/S_USA.TrailNFS_Publish.zip) Trail dataset. These are hiking trails
not open to motor vehicles. Currently much of this dataset has empty
fields, but the trail name and reference number is useful. This
utility is to support the OpenStreetMap US [Trails Initiative](https://openstreetmap.us/our-work/trails/).
