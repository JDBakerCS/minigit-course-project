## Approved UN/UR Baseline

## User needs

| ID | Stakeholder need |
| :---- | :---- |
| UN-GIT-01 | A student developer needs a way to start tracking a local project because it has no recorded history. |
| UN-GIT-02 | A student developer needs to know which project files have changed because they may forget what they edited before recording a checkpoint. |
| UN-GIT-03 | A student developer needs to inspect changed content before recording it because a file may contain unintended edits. |
| UN-GIT-04 | A student developer needs to choose the file content to include in the next checkpoint because later edits may still be unfinished. |
| UN-GIT-05 | A student developer needs to record a meaningful checkpoint because they want to preserve a known project state and explain its purpose. |
| UN-GIT-06 | A student developer needs to review earlier checkpoints because they want to understand how the project reached its current state. |
| UN-GIT-07 | A student developer needs invalid commands to explain why they failed while preserving existing project files and recorded checkpoints. |

## User requirements

| ID | User-visible capability | Need |
| :---- | :---- | :---- |
| UR-GIT-01 | A student developer shall be able to initialize tracking in the current local project folder without removing existing project files. | UN-GIT-01, UN-GIT-07 |
| UR-GIT-02 | A student developer shall be able to see whether project files are untracked, staged, changed after staging, modified, deleted, or clean. | UN-GIT-02 |
| UR-GIT-03 | A student developer shall be able to view differences between current working file content and the content selected for the next checkpoint. | UN-GIT-03 |
| UR-GIT-04 | A student developer shall be able to view differences between content selected for the next checkpoint and the latest recorded checkpoint. | UN-GIT-03 |
| UR-GIT-05 | A student developer shall be able to select the current content of one existing project file for the next checkpoint without selecting unrelated files. | UN-GIT-04 |
| UR-GIT-06 | A student developer shall be able to create a checkpoint of selected content with a nonempty explanation while leaving later unselected edits in the working files. | UN-GIT-05, UN-GIT-04 |
| UR-GIT-07 | A student developer shall be able to view recorded checkpoints from newest to oldest, including their identifier and explanation. | UN-GIT-06 |
| UR-GIT-08 | A student developer shall receive a useful error when a command is invalid, a requested file is unavailable, or a path is outside the allowed project files. | UN-GIT-07 |
| UR-GIT-09 | A student developer shall be able to retry an operation after a failure without losing ordinary project files or an already recorded checkpoint. | UN-GIT-07 |

## Functional System Requirements

SR-01 (source UR-GIT-01): Given a project folder containing an existing file, when the student uses `init`, MiniGit shall initialize tracking in that folder without removing or changing the existing file.

Check: Run `init`, inspect the output, and verify that the existing file is still present and unchanged.


SR-02 (source UR-GIT-08, UR-GIT-09): Given an already initialized project with an existing file and recorded checkpoint, when the student uses `init` again, MiniGit shall report a recognizable error and preserve the existing file and checkpoint.

Check: Run `init` again, inspect the error, and verify that the existing file and recorded checkpoint remain unchanged.


SR-03 (source UR-GIT-05): Given an initialized project with `notes.txt` containing `ONE` and `plan.txt` present, when the student uses `add notes.txt`, MiniGit shall stage a copy of `notes.txt` containing `ONE` without staging `plan.txt`.

Check: Inspect the staged content to verify that `notes.txt` contains `ONE` and `plan.txt` is not staged.


SR-04 (source UR-GIT-08, UR-GIT-09): Given an initialized project with `notes.txt` staged as `ONE` and an existing checkpoint, when the student uses `add missing.txt` and that file does not exist, MiniGit shall report a recognizable error, leave staged `notes.txt` as `ONE`, and preserve the earlier checkpoint.

Check: Inspect the error, verify that staged `notes.txt` still contains `ONE`, and verify that the earlier checkpoint remains.


SR-05 (source UR-GIT-02): Given an initialized project with `notes.txt` staged, when the student uses `status`, MiniGit shall identify `notes.txt` as staged without changing the file’s working or staged content.

Check: Inspect the status output and compare the working and staged copies of `notes.txt` to verify that neither changed.


SR-06 (source UR-GIT-03): In the case of a project that has already been set up and where the `notes.txt` file contains `ONE` in the staged version and `TWO` in the working file after a subsequent edit, if the student uses diff, MiniGit must show a before-and-after comparison of the entire file, displaying the differences without altering either copy of the file.

Check: Inspect the `diff` output for the whole-file comparison between staged `ONE` and working `TWO`, then verify that both copies remain unchanged.


SR-07 (source UR-GIT-04): If the project is initialized and the most recent checkpoint has `notes.txt` with `ONE` while the stage has notes.txt with `TWO`, then when the student uses diff --staged, MiniGit must show a before-and-after comparison of the entire file between the checkpoint and the staged version without altering either of the two copies.

Check: Inspect the `diff --staged` output for the comparison between checkpoint `ONE` and staged `TWO`, then verify that neither copy changed.


SR-08 (source UR-GIT-06): If a project has been initialized and both `notes.txt` is staged while `plan.txt` is not selected in the working files, then when the student enters commit -m "save notes", MiniGit must create a checkpoint with that message including the content of the staged `notes.txt` and at the same time leave the `plan.txt` unchanged in the working files.

Check: Inspect the new checkpoint for the message and staged `notes.txt` content, then verify that `plan.txt` remains unchanged in the working files.


SR-09 (source UR-GIT-08, UR-GIT-09): Given an initialized project with notes.txt staged as ONE and an existing checkpoint, when the student uses commit -m "", MiniGit shall report a recognizable error and preserve both the staged `notes.txt` content and the earlier checkpoint.

Check: Run `commit -m ""`, inspect the error, and verify that staged `notes.txt` still contains `ONE` and the earlier checkpoint remains.


SR-10 (source UR-GIT-07): Given an initialized project with two recorded checkpoints, each having an identifier and explanation, when the student uses log, MiniGit shall display the checkpoints from newest to oldest with each identifier and explanation.

Check: Inspect the `log` output and verify the checkpoint order, identifiers, and explanations.


SR-11 (source UR-GIT-02): Given an initialized project where `notes.txt` contains `ONE` in the stage and TWO in the working file after a later edit, when the student uses status, MiniGit shall identify `notes.txt` as changed after staging without changing either copy.

Check: Inspect the status output for the changed-after-staging state, then verify that the staged content is still `ONE` and the working content is still `TWO`.


SR-12 (source UR-GIT-06): Given an initialized project where `notes.txt` contains `ONE` in the stage and `TWO` in the working file after a later edit, when the student uses commit -m "save staged version", MiniGit shall create a checkpoint containing `ONE` while leaving the working `notes.txt` content as `TWO`.

Check: Inspect the new checkpoint to verify that it contains `ONE`, then verify that the working `notes.txt` still contains `TWO`.
