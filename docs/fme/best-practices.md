## Best Practices



### Readers

Readers are generally fairly straightforward, but sometimes you will run into issues with them. You should follow these practices to avoid hitting a snag.

#### If Reading From A Geospatial Database Choose The Geospatial Reader

Many times a database, like SQL Server, will have a non-spatial and spatial reader. If you are reading geospatial data, choose the spatial reader. If your data is non-spatial, choose the non-spatial reader. 

This is the most confusing where the non-spatial and spatial reader name, like for SQL Server, are very similar.

#### Set A Timeout

If you set a timeout of zero for the reader, the reader will attempt to read from the data source forever. It is generally ok if you do this while you are working inside FME. However, if you run this workflow from the master workflow, the potential is there for the workflow to not ever stop running.

Setting your timeout to 30 seconds is generally good. If you find that your reader needs more time, set a higher timeout.

### Workflow Scheduling

If you have several workflows that need to run periodically, you will need to schedule them with some sort of mechanism. Windows offers the task scheduler. OS X and Linux both use cron for this. You could schedule each workflow to run individually. However, there are other ways of scheduling workflows that have been found to be very beneficial.

#### Master Workflow

Safe FME has the ability to do batch processing. You can take advantage of this by creating a master workflow that reads in an index of all workflows, and runs each one.

You can use a CSV reader to read in a CSV where each record represents a workflow you want automated. Each record in the CSV will need to contain the full path to a workflow.

The CSV will then be piped into a [WorkspaceRunner](http://docs.safe.com/fme/html/FME_Transformers/FME_Transformers.htm#Transformers/workspacerunner.htm) that will run each workflow.

From here if you wish, you can use the Socrata writer to write to a dataset that keeps record of all of your workflow failures and successes as well as for how long it took to run them.

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
