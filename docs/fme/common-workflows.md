## Common Workflows

There are four common workflows that we have encountered while automating data: basic, geospatial (point), geospatial (polygon, and etc.), and SQLCreator.

All workflows use the [Socrata writer](http://dev.socrata.com/publishers/examples/fme-socrata-writer.html) except for the geospatial (polygon, and etc.) workflow.

### Basic

This is the most basic workflow. It requires, at the very least, a basic [reader](http://docs.safe.com/fme/html/FME_Workbench/FME_Workbench.htm#Workbench/reader_adding_as_resource.htm) and Socrata writer.

### Geospatial (Point Data)

This workflow requires use of a geospatial reader. You will also need, at least, a [CoordinateExtractor](http://docs.safe.com/fme/html/FME_Transformers/FME_Transformers.htm#Transformers/coordinateextractor.htm) for extracting latitude and longitude, [AttributeReprojector](http://docs.safe.com/fme/html/FME_Transformers/FME_Transformers.htm#Transformers/attributereprojector.htm) to project the coordinates into EPSG:4326/LL84, a [StringConcatenator](http://docs.safe.com/fme/html/FME_Transformers/FME_Transformers.htm#Transformers/stringconcatenator.htm) for making a Location column, and a Socrata writer.

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
