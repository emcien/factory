# Emcien Factory

This repository contains the generalized template for building automation
factories using Emcien products, as well as some boilerplate factories that can
be used as templates and / or imported into Emcien Connect or Emcien Scheduler.
To that end, it also contains a small set of bash scripts to aid in automating
some of the factory buildout.

## Docs

* [Job and State Tracking](docs/jobs.md): the basic building block of a factory
  is encapsulated in a "job", which includes the actual business logic of the
  job itself, the triggering mechanism for the job and some method to track job
  state.

* [Generic Factory](docs/generic_template.md): using a set of jobs that are
  intended  to work in sequence, you can build a "factory" which integrates
  with the customer's systems as both input and output of the factory.

* [Error Handling](docs/error_handling.md): all pieces of the factory need to
  implement careful and thoughtful error handling. Without this, the factory
  can a) breakdown and begin to behave unexpectedly and b) do so silently
  without any means to know that it is not working.

* [Noficiations](docs/notifications.md): While the factory should be able
  provide significant automation, that does not mean "set it and forget it".
  Data and process can change. But if a factory has simple ways to notify end
  users of normal and abnormal events in the factory, those changes will be
  easy to detect.

* [Configuration](docs/config.md): Rather than hard-coding configurable values
  that are a) customer or implementation specific and / or b) subject to change
  over time, the factories code should store and access a centralized
  configuration.

* [Clean Up](docs/cleanup.md): There are often parts of a factory that leave
  traces of its activities in that factory itself or in external systems, such
  as inside of Emcien products. Using periodic clean up jobs to remove these
  artifacts will help the maintenance and management of the factory and its
  internal data as well as ensure that the resources that power the factory do
  not become exhausted (memory, disk space, I/O, etc).

## Factory Checklist
Regardless of the use case that is being built, building automation around
Emcien products follows a standard pattern and architecture. There are many
ways to implement this pattern and while the templates we provide will be in
the context of Emcien Connect and Emcien Schedule, it could also be done with
basic scripts and cron jobs or other scheduling solutions. As such, replace
"stored procedure", "table", etc with the analagous concepts for alternative
implementations.

### General
- [ ] A specific user for running factories
- [ ] A standardized configuration table
- [ ] Error table

### Error Handling
- [ ] Error handling for generic internal errors
      - [ ] Stored procedure errors
      - [ ] External system call failures
      - [ ] HTTP API call failures
- [ ] Error handling for Emcien failures
      - [ ] Job initialization failures
      - [ ] Build job failures

### Jobs
- [ ] Custom prepare job(s) (customer system integration)
- [ ] Emcien build job
- [ ] Emcien check job
- [ ] Emcien ready job
- [ ] Custom processing job(s) (customer system integration)
- [ ] Clean up job(s)
- [ ] State tables for each job
