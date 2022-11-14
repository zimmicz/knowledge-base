## Subtasks
[Database 1] Migration for `flexpoolOnly` column with default `false`
[Backend 1] Let `JobService` accept `flexpoolOnly` for creation, but do not enforce it to be present just yet
[Backend 2] Create `makeJobFlexpoolOnlyService` that is going to be run as part of `JobService.update`, because we want ES (?)
[Backend 1,2] Create integration tests for `flexpoolOnly` flag on **controller** level
- https://miro.com/app/board/uXjVPLFWLv4=/?moveToWidget=3458764537085526742&cot=14
- https://miro.com/app/board/uXjVPLFWLv4=/?moveToWidget=3458764537085770802&cot=14
- https://miro.com/app/board/uXjVPLFWLv4=/?moveToWidget=3458764537086001542&cot=14