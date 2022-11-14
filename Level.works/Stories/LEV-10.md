Implemented in a feature branch!

## Subtasks
[Database] Migration for `flexpoolOnly` column with default `false`
[Backend] Deliver `flexpoolOnly` flag to shift planning, job list and shift detail in OGP and shift creation/edit form
[Frontend] Display `flexpoolOnly` icon on job card, shift detail and shift card on planning
[Frontend] Create toggle on shift creation/editing with the default value of `false`
[Backend] Let `JobService` accept `flexpoolOnly` for creation
[Backend] Create `makeJobFlexpoolOnlyService` that is going to be run as part of `JobService.update`, because we want ES (?)
[Backend] Create integration tests for `flexpoolOnly` flag on **controller** level (test controller.method)
- https://miro.com/app/board/uXjVPLFWLv4=/?moveToWidget=3458764537085526742&cot=14
- https://miro.com/app/board/uXjVPLFWLv4=/?moveToWidget=3458764537085770802&cot=14
- https://miro.com/app/board/uXjVPLFWLv4=/?moveToWidget=3458764537086001542&cot=14