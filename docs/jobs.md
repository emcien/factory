# Jobs and State Tracking

A job is the basic building block of a factory. It encapsulates:

* the business logic of the job itself (what it does)
* the triggering mechanism for the job (via schedule or explicit call)
* state tracking of a job

Ideally, a job should not need to have any knowledge about other jobs other
than the data that is passed to the job via it's trigger. Here is a diagram of
a basic job execution flow:

![generic_job](img/generic_job.png)
