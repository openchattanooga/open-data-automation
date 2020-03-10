## Workflow Organization

### A Single Workflow Project

A single workflow project is usually a part of a large number of other workflows. It is good for them to be organized in a consistent manner.

#### Workflow Runner

This is an FME workflow that runs the project's main workflow. This is the actual workflow that is scheduled to run by the master workflow or placed directly on a scheduler.

The name of this file for each workflow project is called `runner.fmw`.

#### Dataset Info

This is a CSV file that includes information about the main workflow including the full filepath to the workflow. The workflow runner reads this file and executes the main workflow from the full filepath included in the dataset info file. 

The name of this file for each workflow project is called `dataset_info.csv`.

The following is an example of the contents of a dataset info file:

```
Job Order,Job Name,Description,Path to fmw file
1,Some Dataset,This is a dataset.,C:\Workflows\Some Category\Some Dataset\somedataset.fmw
```

#### Main Workflow

This is the project's main FME data extraction workflow. These workflows can be run independently if needed. So it is best to give the filename of the workflow something close to the name of the actual dataset instead of something generic.

### Grouping Multiple Workflows

The following directory organization has been followed: `All Workflows → Entity Name →  Dataset Name`

`All Workflows` is a directory that contains all of our workflows. `Entity name` is a directory named after the entity/organization that the dataset comes from. `Dataset Name` is a directory that is named after the actual dataset and contains all of dataflow project's files.

For instance, we have the Building Permit dataset from Economic and Community Development. Our directory that contains all workflows called `Workflows`. Assuming our Workflow directory is located on the root of some drive, for example `G:`, our file path might look like: `G:\Workflows\Economic and Community Development\Building Permit\`.  
