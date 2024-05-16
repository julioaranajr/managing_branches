# Managing branches

A single Git repository can maintain multiple branches of development. To create a new branch named experimental, use
```sh
$ git branch experimental
```
If you now run
```sh
$ git branch
```
you’ll get a list of all existing branches:
```sh
  experimental
* master
```
The experimental branch is the one you just created, and the master branch is a default branch that was created for you automatically. The asterisk marks the branch you are currently on; type
```sh
$ git switch experimental
```
to switch to the experimental branch. Now edit a file, commit the change, and switch back to the master branch:
```sh
(edit file)
$ git commit -a
$ git switch master
```
Check that the change you made is no longer visible, since it was made on the experimental branch and you’re back on the master branch.

You can make a different change on the master branch:
```sh
(edit file)
$ git commit -a
```
at this point the two branches have diverged, with different changes made in each. To merge the changes made in experimental into master, run
```sh
$ git merge experimental
```
If the changes don’t conflict, you’re done. If there are conflicts, markers will be left in the problematic files showing the conflict;
```sh
$ git diff
```
will show this. Once you’ve edited the files to resolve the conflicts,
```sh
$ git commit -a
```
will commit the result of the merge. Finally,
```sh
$ gitk
```
will show a nice graphical representation of the resulting history.

At this point you could delete the experimental branch with
```sh
$ git branch -d experimental
```
This command ensures that the changes in the experimental branch are already in the current branch.

If you develop on a branch crazy-idea, then regret it, you can always delete the branch with
```sh
$ git branch -D crazy-idea
```
Branches are cheap and easy, so this is a good way to try something out.
