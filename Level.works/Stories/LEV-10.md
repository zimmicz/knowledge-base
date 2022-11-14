Implemented in a feature branch!

## Subtasks
[Database] Migration for `flexpoolOnly` column with default `false`
[Backend] Deliver `flexpoolOnly` flag to shift planning, job list and shift detail in OGP and shift create/edit form
	[Frontend] Display `flexpoolOnly` icon on job card, shift detail, shift card on planning and shift create/edit form
[Backend] Let `JobService.create` accept `flexpoolOnly` flag
[Frontend] Create toggle on shift creation with the default value of `false`
[Backend] Create `UpdateJobService` (check flexpoolOnly is set to true) in the same spirit as Archival thing
[Frontend] Create toggle on shift edit with the default value coming from the backend
[Backend] Fail new shift application on `flexpoolOnly` job automatically (edge case)
[Backend] Create integration tests for `flexpoolOnly` flag on **controller** level (test controller.method)
- https://miro.com/app/board/uXjVPLFWLv4=/?moveToWidget=3458764537085526742&cot=14
- https://miro.com/app/board/uXjVPLFWLv4=/?moveToWidget=3458764537085770802&cot=14
- https://miro.com/app/board/uXjVPLFWLv4=/?moveToWidget=3458764537086001542&cot=14
[App] hide shifts for flexpoolOnly jobs from non-members of flexpool