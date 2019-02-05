# PROJECT SETTINGS AND STRUCTURE

1. `master` should *NEVER* be directly committed if you don't know what are you doing.

2. Any development phases should be committed to correct sub-branches:
- `features`: new implementations.
- `hotfixes`: bug fixings.
- `releases`: offical releases.

3. Always follow these steps before committing:
- While on `features/...`, merge `master` back to current branch.
- After resolve all conflicts, create `pull request` to the reviewer.

4. Branch should follow this pattern:
- `<sub-branch>\<YYYYMMDD>_summary_of_task_<your-git-username>`