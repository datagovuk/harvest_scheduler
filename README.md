# Harvest scheduler

The Harvest Scheduler is response for publishing harvest [jobs](https://github.com/datagovuk/dgu_harvesters#jobs) onto a message queue for processing by [harvesters](https://github.com/datagovuk/dgu_harvesters). The jobs are published on a schedule that is defined by the database model, which itself is created by an external process.

## Process

The scheduler should load entries from the database, making sure to keep local copies up to date with the source database (model tbd)

Each entry should contain the schedule it is run on (every X hours), the date/time of the last run  and a blob representing the message to be added to the queue.

When it is time for an entry to be executed the blob is pushed onto the configured queue, and the entry is updated and then re-scheduled.

## Potential extra functionality

* It should be possible to push a blob to the scheduler for immediate execution to allow for testing/dry-runs.

* A web-based UI simply listing the schedule at any given time (so we can check what is due when) would be useful.


## Database structure

TBD but should contain enough data for the scheduler to be able to work out when to next push the blob onto a queue.

## Required configuration

* Access to a database
* Configuration of the message queue to be used




