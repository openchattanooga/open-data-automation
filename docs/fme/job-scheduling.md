## Workflow Scheduling

If you have several workflows that need to run periodically, you will need to schedule them with some sort of mechanism.  You could schedule each workflow to run individually. However, there are other ways of scheduling workflows that have been found to be very beneficial.

#### Master Workflow

Safe FME has the ability to do batch processing. You can take advantage of this by creating a master workflow that reads in an index of all workflows, and runs each one.

You can use a CSV reader to read in a CSV where each record represents a workflow you want automated. Each record in the CSV will need to contain the full path to a workflow.

The CSV will then be piped into a [WorkspaceRunner](http://docs.safe.com/fme/html/FME_Transformers/FME_Transformers.htm#Transformers/workspacerunner.htm) that will run each workflow.

From here if you wish, you can use the Socrata writer to write to a dataset that keeps record of all of your workflow failures and successes as well as for how long it took to run them.

#### Job Management

Depending on your operating system, there are many choices for job management. Out of the box, Windows offers the task scheduler. OS X and Linux both use cron. You will need to schedule jobs, monitor them, and potentially stop jobs that may not have stopped for whatever reason. 

##### Windows Task Scheduler and Task Manager

The task scheduler can be accessed by opening the `Control Panel`, then going to `Administrative Tools`. The most comprehensive documentation for Windows' Task Scheduler is located [here](https://msdn.microsoft.com/en-us/library/windows/desktop/aa383614(v=vs.85).aspx). Reading that will answer any question you will have about the Task Scheduler, but we'll go over common use cases below.


###### Creating A Task

The easiest way to create a task is to use the "Create Basic Task Wizard" by going to `Action` in the file menu then clicking `Create Basic Task`. From here, you can specify when the task should run. It will also ask you what program you want to run. For automating a Safe FME workflow, you will want to enter something like the following: `fme.exe c:\some\filepath\to\your\workflow.fmw`.

###### Stopping A Task

There will be occasions where a workflow may not stop running. You should first check if the scheduled task is still running by opening up the scheduler. Check the "Last Run Result" of your job. If it's finished, it should say something like "The operation completed successfully." Otherwise, try right clicking on the task and then left click "End".

If that doesn't work. Open up the Windows Task Manager. You can get to the Windows Task Manager by pressing Ctrl+Shift+Esc at the same time.

When you have the Task Manager open, look in the "Processes" tab for any instances of `FME.exe` or `fme.exe`. If you don't have Safe FME open, those are likely workflows that are still trying to run. To end a task, right click on it then left click "End task". Use this to close any instances of `FME.exe` or `fme.exe`.   
