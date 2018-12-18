## Common Workflows

There are four common workflows that we have encountered while automating data: basic, geospatial (point), geospatial (polygon, and etc.), and SQLCreator.

All workflows use the [Socrata writer](http://dev.socrata.com/publishers/examples/fme-socrata-writer.html) except for the geospatial (polygon, and etc.) workflow.

### Basic

This is the most basic workflow. It requires, at the very least, a basic [reader](http://docs.safe.com/fme/2017.1/html/FME_Desktop_Documentation/FME_Workbench/Workbench/readers_adding.htm) and Socrata writer.

### Geospatial (Point Data)

This workflow requires use of a geospatial reader. You will also need, at least, a [CoordinateExtractor](https://www.safe.com/transformers/coordinate-extractor/) for extracting latitude and longitude, [AttributeReprojector](https://www.safe.com/transformers/attribute-reprojector/) to project the coordinates into EPSG:4326/LL84, a [StringConcatenator](https://www.safe.com/transformers/string-concatenator/) for making a Location column, and a Socrata writer.

Your point columns should be represented by the following names and types:
* Latitude
  * Type: Number
* Longitude
  * Type: Number
* Location
  * Type: Location

### Geospatial (Polygons, and etc.)

**TODO**

### SQLCreator

This workflow uses the SQLCreator "reader" and a Socrata writer at the minimum. It is different from a normal reader such that you have more control over your data source via SQL for complex joins and the like. You should use this if you have existing workflows already utilizing SQL. 
