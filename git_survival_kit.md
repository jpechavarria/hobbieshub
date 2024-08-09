# Git survival kit

## One time tasks

1. Install git
2. Register user in git version control platform (Github, Gitlab, Bitbucket, Codecommit, etc).
3. SSH key registering in git version control platform (Github, Gitlab, Bitbucket, Codecommit etc.). Make sure you have a SSH key. Steps using terminal: (in Windows use git bash):
  * Check if you already have one:
      `ls -al ~/.ssh`
    If you don’t, generate a new SSH key and adding it to the ssh-agent:
      
      - Classic way:
        `ssh-keygen -o -t rsa -b 4096 -C "email@example.com"`
      
      - New way:
        `ssh-keygen -t ed25519 -C "email@example.com"`
      
      Copy and paste into github (or Gitlab, Bitbucket, Codecommit etc.) settings (just the public key `.pub`):
         `cat ~/.ssh/id_rsa.pub`

4. Clone repository:
   `git clone <repo_url.git>`
   example:
   `git clone git@github.com:jpechavarria/hobbieshub.git`

5. Set global user name & global email:
   * `git config --global user.name "<your name>"`
     * example: `git config --global user.name "Johann Echavarria"`
   * `git config --global user.email "<your email>"`
     * example: `git config --global user.email "email@example.com"`

## Day to day tasks, new feature, bug fix, ticket etc

1. Make sure your branch changes are clean:
  `git status`
  You should see something similar to:
  `nothing to commit, working tree clean`
  If it's not clean you can clean it in several ways, one is to run:
  `git checkout .`
2. Go to your working branch, usually something similar to `develop`, not `master` or `main` because they use to be production. So run
   `git checkout develop`
3. Update your local repository
   `git pull` or `git pull origin` or `git pull origin/develop`
4. Create a new branch with an appropriate name (usually the name of the ticket)
  `git checkout -b ticket-007`
5. Do your changes (coding work) normally.
6. Before commiting the changes normally you check that tests and linters work with a couple of commands (not needed in this exercise).
7. `git status` make sure you are not on in master or main but in your branch.
8. `git diff` view differences with the branch and perform an auto code review.
9. `git add -A` # to stage all changes (or `git add path/to/file.txt` to add a
file individually)
10. `git status` # to check again that all the changes are staged to be committed locally
11. `git commit -m "Your message or commit description"`
12. `git push` or `git push origin ticket-007` to send your changes or create the branch in the server
13. This steps can also be done with different commands and a lot of visual tools like `git citool` or `vscode` and others.
14. To create a a pull request go to the url of Github (or equivalent) repo and you should see the new feature branch ticket-007, with a "Compare and Pull Request" button (in Gitlab they say "merge request").
15. Click on the button and you see a url with the diffs (similar to the local command `git diff`). This another oportunity to do an auto code review.
16. Write the description of your changes.
17. Make sure that the source and target branches are correct and click on “Create Pull Request” when ready.


# Some usefull commands

## Restore a file like in HEAD
  `git checkout HEAD -- FILE_NAME`
Example:
  `git checkout HEAD -- yarn.lock`

# Restore a file like in some branch or commit
  Branch:
    `git checkout origin/<some-branch> -- src/file.js`
  Commit
    `git checkout bcf00d174c0b286b70d7be45b6868fb917dbc37b --src/routes/index.js`



## Take a commit from another branch and apply to the current branch:

  `git cherry-pick <commit-hash>`

## Revert a commit
  `git revert` or `git revert HEAD`

## Check git log
  `git log`
Or
  `git log --oneline`
You can advance in history pressing enter and you can exit pressing the "q" key.
