## Best Practices

These are good guidelines to go by when setting up a workflow for automation. Following these guidelines will generally prevent you from falling into certain pitfalls mentioned below.

### Readers

Readers are generally fairly straightforward, but sometimes you will run into issues with them. You should follow these practices to avoid hitting a snag.

#### If Reading From A Geospatial Database Choose The Geospatial Reader

Many times a database, like SQL Server, will have a non-spatial and spatial reader. If you are reading geospatial data, choose the spatial reader. If your data is non-spatial, choose the non-spatial reader. 

This is the most confusing where the non-spatial and spatial reader name, like for SQL Server, are very similar.

#### Set A Timeout

If you set a timeout of zero for the reader, the reader will attempt to read from the data source forever. It is generally ok if you do this while you are working inside FME. However, if you run this workflow from the master workflow, the potential is there for the workflow to not ever stop running.

Setting your timeout to 30 seconds is generally good. If you find that your reader needs more time, set a higher timeout.

### Dates And Times

#### Convert Dates and Times To ISO 8601

Use the [DateTimeConverter](https://docs.safe.com/fme/html/FME_Desktop_Documentation/FME_Transformers/Transformers/datetimeconverter.htm) transformer to convert date/time columns into a standard date/time format. Socrata understands [several date/time formats](https://support.socrata.com/hc/en-us/articles/202949918-Importing-Data-Types-and-You-), but it is best to adhere to ISO 8601 as much as possible.

### Geospatial Data

#### Ensure Geospatial Data is Projected To EPSG:4326/LL84

Many times geospatial will be stored in a regionally relevant coordinate reference system. In our case: EPSG:2274. You should always re-project to EPSG:4326/LL84 unless there is a very good reason not to do so.

### Scripting

The ability to write code in your workflows is very powerful. However, you should heed to these recommendations.

#### Use A Transformer When Possible

It is very likely there already exists a transformer for something that you want to do. You should search the [FME knowledgebase](https://knowledge.safe.com/knowledgeoverview) and double check before you start writing code.

If a transformer for your problem doesn't exist, then go ahead. A notable example we've run into where we've needed to write code is pulling data from SFTP servers. FME does not support the SFTP protocol out of the box.

#### Use Python, Not TCL

There is nothing wrong with TCL. Both Python and TCL both seem to be well supported. However, if you get stuck, you will more likely find help with Python than with TCL.

Also, there are a myriad of libraries for Python. There is likely already a library for what you want to do.

#### Follow Standard Python Style Convention

Follow the [PEP8](https://www.python.org/dev/peps/pep-0008/) Python style guide for writing clear code.
