# Homework 2 — Part 2 Submission

Student name: James Baker

GitHub username: JDBakerCS

## 1. Git Command Observations

| Command or workflow            | What did you observe?                                                                      | What was the user trying to accomplish?                                                       | What problem or risk did it address?                                                 |
| ------------------------------ | ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| 1. `git status`                | It shows which files I changed, which ones are staged, and which ones are untracked.       | The user is trying to see the current state of their work before doing anything else with it. | It keeps you from forgetting a file or committing something you didnt mean to.       |
| 2. `git diff`                  | I can see the actual changes I made to my files that havent been staged yet.               | The user is trying to check what they changed before deciding what to do with it.             | It gives you a chance to catch mistakes or changes you didnt mean to make.           |
| 3. `git add <file>`            | The file I select gets staged and is now ready to be included in the next commit.          | The user is trying to choose which work they want included in the next saved version.         | It helps keep unfinished or unrelated changes out of a commit.                       |
| 4. `git commit -m "<message>"` | The staged changes are saved together as a new version with a message describing the work. | The user is trying to save a completed point in their work and describe what they changed.    | It gives the user a saved version of their work and a way to identify what was done. |

## 2. User Needs

### UN-GIT-01 — Know Current Project Status

> A developer needs a way to see the current state of their project because they need to know what they have changed before saving their work.

### UN-GIT-02 — Check Changes Before Saving

> A developer needs a way to review the changes they made because they might have made a mistake or changed something they dont want to save.

### UN-GIT-03 — Control What Goes Into a Commit

> A developer needs to select which related changes will be included in next commit, so unfinished or unrelated work can remain outside that commit.

## 3. User Requirements

| ID and short title              | User requirement                                                                                              | Source user need | Rationale                                                                                    |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------- | ---------------- | -------------------------------------------------------------------------------------------- |
| UR-GIT-01 — View Project Status | A user shall be able to see which project files have been changed and which changes are selected to be saved. | UN-GIT-01        | This lets the user know where their project currently stands before they save anything.      |
| UR-GIT-02 — Review Changes      | A user shall be able to see what changed in their project files before saving a new version.                  | UN-GIT-02        | This gives them a chance to find mistakes or changes they didnt mean to make.                |
| UR-GIT-03 — Select Changes      | A user shall be able to choose which changed files will be included in the next saved version.                | UN-GIT-03        | Some changes might still be unfinished and shouldnt be included yet.                         |
| UR-GIT-04 — Save a Version      | A user shall be able to save their selected changes as a new version with a message describing the work.      | UN-GIT-03        | This keeps completed changes together and makes it easier to understand what was done later. |
