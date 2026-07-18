# Install

1. Create the source directory.
1. `sudo apt install git`

# Configure

1. Update the Git configuration:
   ```
   git config --global user.email "andrei@montchik.net";
   git config --global user.name "Andrei Montchik";
   git config --global pull.rebase false;
   ```
1. Confirm that the config change was applied: `git config --list`

# Clone

1. [Add the SSH pubkey](Linux.md#ssh) to GitHub account: https://github.com/settings/keys
1. Check SSH access: `ssh -vT git@github.com`
1. request to add your Git account as collaborator to GitHub repo
1. Use SSH to clone GIT repos

# Branch

- Show remote branches: `git branch -r`
- Create:
  - Create Local Branch: `git checkout -b <new-branch-name>`
  - Push to remote repo: `git push --set-upstream origin <new-branch-name>`
  - Branch from the commit: `git checkout -b <new branch name> <commid id>`
  - Check if remote branch exists: `git branch -r | grep <branch name>`
- Remove:
  - Local: `git branch -d <branch name>`
  - Remote: `git push origin --delete <brach name>`

# Cleanup

- `git remote prune origin` Or `git fetch origin --prune`
- Remove all untracked files: `git clean -fdx`

# Diff

- File names only: git diff --name-only release/raptor
- Specific file: git diff release/raptor raptor-cgw/api/src/main/scala/com/gemini/raptor/cgw/api/DomainEntries.scala
- Between branches:
  1. git fetch
  1. git log --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --graph --grep="CGW" 'origin/release/2022-07-06'...'origin/release/2022-07-20'
- Between commits:
  - `git diff b509834813184d3be0f1e536ed9275ef2ec57610 80c88fb6c407135223644d0d99bb504d980bc4f1 --name-only`
  - `git diff b509834813184d3be0f1e536ed9275ef2ec57610 80c88fb6c407135223644d0d99bb504d980bc4f1 cpp/bin/env`
- Between tags:
  ```
    git diff --color-moved-ws=ignore-all-space,ignore-space-change,ignore-space-at-eol trading-release-dist-744..trading-release-dist-755 -- \
   'raptor-sbe-api/*' \
   'raptor-commons/api/*' \
   'raptor-cgw/*' \
   'raptor-cgwr/*'
  ```

# Stash

- Save: git stash push -m "my_stash"
- View: git stash list
- Pop: git stash pop --index <index>
- Remove all stashed: git stash clear

# Commit

- Add new files: `git add .`
- Review changes in the specific commit: `git show <commit-hash>`
- Show changes in local commits: `git log origin/main..HEAD -p`
- Discard the uncommitted change: `git checkout -- <filename>`
- Undo the last commit:
  - Preserve the changes as uncommitted: `git reset --soft HEAD~1`
  - Discard the changes: `git reset --hard HEAD~1`
- Undo a single file: `git checkout [commit ID] -- path/to/file`
- Merge the specific commit: `git cherry-pick <commit id>`
- Check which branches contains the commit: `git branch -a --contains <commit id>`
- Show Last n commits: `git log --pretty-oneline | head -n`
- Show all files in the commit: `git show --pretty="" --name-only <commit id>`
- Show Commits containing the search line: `git log -S LegacyMessageHandler`

## Signing Commits

- Configure: https://gemini-spaceship.atlassian.net/wiki/spaces/DEV/pages/858859/Developer+Setup#DeveloperSetup-commit-signingGitCommitSigningConfiguration
- Troubleshoot: https://gemini-spaceship.atlassian.net/wiki/spaces/DEV/pages/2323644429/Commit+signing+troubleshooting
- Restart SSH Agent: killall ssh-agent; eval `ssh-agent -s`; /usr/bin/ssh-add -s /usr/local/lib/opensc-pkcs11.so
- Disable GPG signing: git config --global commit.gpgsign false
- Make sure that the signing is enabled: `git config --global commit.gpgsign` should return `true`

# Merge

Merge from the remote branch:
git merge --no-edit origin/master
git merge --no-ff --no-commit -s recursive -X patience origin/release/raptor

# Push

Use git push --force-with-lease instead of git push --force to update a branch where you have changed history.

# Tag

https://git-scm.com/book/en/v2/Git-Basics-Tagging

- `git tag -a <tag name> -m <Tag description>`
- `git push origin <tag name>`
- to review: `git show <tag name>`
- to checkout: `git checkout <tag name>`
