## Subtasks
[Database] Migration for `flexpoolOnly` column with default `false`
[Backend] Let `JobService` accept `flexpoolOnly` for creation, but do not enforce it to be present just yet
[Backend] Create `makeJobFlexpoolOnlyService` that is going to be run as part of `JobService.update`
[Backend] Let JobService accept 