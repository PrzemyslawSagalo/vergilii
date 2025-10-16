# Git Cheat Sheet

## Safely Undoing Commits on a Shared Branch

1.  **Create a "Fix" Branch**

    Always perform reverts on a separate branch. This allows for a Pull Request, enabling team review and CI checks.

    ```bash
    git checkout main
    git pull origin main
    git checkout -b fix/revert-accidental-commits
    ```

2.  **Revert the Unwanted Commits**

    Create new commits that undo the changes from the old, unwanted ones.

    ```bash
    # Revert specific commits by listing their SHAs
    git revert <commit-hash-1>
    git revert <commit-hash-2>
    ```

3.  **Resolve Conflicts (If They Occur)**

    a. **Open the conflicted file.** You'll see conflict markers:
       * `<<<<<<< HEAD`: The current code, **including** the mistake you're reverting.
       * `=======`: A separator.
       * `>>>>>>> parent of ...`: The code as it was **before** the mistake.

    b. **Manually edit the code** to the desired final state. This often means combining changes from both sections.

    c. **Finalize the revert:**

        ```bash
        # Stage your manually fixed file(s)
        git add <path/to/your/resolved/file.py>

        # Continue the revert process
        git revert --continue
        ```

       **Safety Escape Hatch:** If you get stuck, you can cancel the process entirely.

        ```bash
        git revert --abort
        ```

4.  **Squash Reverts into a Single Commit**

    Clean up your branch history by combining the multiple "Revert..." commits into one clear, atomic commit.

    a. **Start an interactive rebase.** If you created 3 revert commits, you'll rebase the last 3.

        ```bash
        # Replace '3' with the number of revert commits you made
        git rebase -i HEAD~3
        ```

    b. **Edit the rebase plan.** Your editor will open. Change `pick` to `s` (for squash) for all commits except the first one.

        ```text
        pick a1b2c3d Revert "wip"
        s d4e5f6g Revert "wip"
        s h7i8j9k Revert "wip"
        ```

    c. **Write a new commit message.** After saving, another editor opens. Write a single, clear message for the combined commit (e.g., `revert(main): Remove accidental WIP commits`).
