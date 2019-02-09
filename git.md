GIT
===

![git data transport](imgs/git.png)

Tutorials
---------

* http://git-scm.com/documentation (official)
* http://learn.github.com/ (basic Code School)
* http://try.github.com/ (basic GitHub)
* https://www.atlassian.com/git/tutorials/advanced-overview (+1)
* http://pcottle.github.io/learnGitBranching/ (+1)
* http://byte.kde.org/~zrusin/git/git-cheat-sheet.svg (cheat-sheet)
* https://github.com/tiimgreen/github-cheat-sheet (cheat-sheet src)
* http://aprendegit.com [ES] (blog)
* https://github.com/git-tips/tips
* http://chris.beams.io/posts/git-commit/

Tips
----
* Pretty log (https://coderwall.com/p/euwpig/a-better-git-log)
```sh
git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

* When a string was added/deleted in the repo.
```sh
git log -S caca
```

* Git alias. Add in `~/.gitconfig`
```ini
[alias]
    lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

* Describe a commit. The output of the command looks like: `<tag>_<numCommits>_g<hash>` Where tag is the closest ancestor tag in history, numCommits is how many commits away that tag is, and <hash> is the hash of the commit being described.
```sh
git describe 2.2.x #2.2.0-75-g16deae8
```

* `Add` and `commit` together.
```sh
git commit -a -m 'msg'
```

* Stage a file hunk
```sh
git add -p file.md
```

* Merge witout commit (no check in prod):
```sh
git merge --no-commit <branch>
git merge --abort
```

* Reset working directory
```sh
git clean -xdf
```

* Create a new branch
```sh
git checkout -b branch_name
```

* List branches ordered by most recent commit.
```sh
git for-each-ref --sort=-committerdate refs/remotes
```

* Find the most recent common ancestor commit of two branches
```sh
git merge-base A B
```

* Checkout your last branch
```sh
git checkout -
```

* Grab a file from another branch without switching branches:
```sh
git checkout <BRANCH> -- path/to/file
```

* Delete remote branch or remote tag
```sh
git push origin :branch-to-delete
git push origin --delete branch-to-delete (git >= 1.7)
```

* Options to set remote-tracking branches
```sh
git branch -u o/master foo #or
git checkout -b totallyNotMaster o/master #or
git push --set-upstream origin totallyNotMasterInOrigin #or edit .git/config
```

* Delete local Git branches after deleting them on origin
```sh
git pull --prune
```

See `git configure remote.origin.prune true`

* Delete commits from the remote repo using other branch (https://youtu.be/mdZvYyIKURo)
```sh
git branch -D master
git push origin :master  #Change github HEAD via web
git checkout -b master
git push origin master
```

* Before you git blame someone, make sure you check one of these (http://code.tutsplus.com/tutorials/git-tips-from-the-pros--net-29799):
```sh
git blame -w  # ignores white space
git blame -M  # ignores moving text
git blame -C  # ignores moving text into other files
```

* Git follow (http://stackoverflow.com/questions/14142609/git-discover-which-commits-ever-touched-a-range-of-lines)
```sh
git log --topo-order --graph -u -L 155,155:file.c
```

* Track changes on a line (additions/deletions)(http://stackoverflow.com/questions/4404444/how-do-i-git-blame-a-deleted-line#4404551):
```sh
git log -S '<DELETED_LINE>' path/to/file
```

* Revert a merge (the `-m` option specifies the parent number starting from 1. )
```sh
git revert -m 1 <commit>...
```

* Find bugs with `bisect` (https://youtu.be/Py8Vf0n3DCY and https://youtu.be/zCRF3tWC4k4)
```sh
git bisect start      #Empiezo proceso
git bisect bad        #Marco actual como malo
git checkout HEAD-30  #Cambio a 30 commits antes
git bisect good       #Tras ver que no tiene el bug, lo marco como bueno
git bisect skip
git bisect run ./test #Para automatizar porceso creo un script con el test que me indica si es bueno o no
git bisect reset      #Recupero estado inicial
git bisect log
git bisect replay git_b_log_file
```

* Reset working directory
```sh
git clean -xdf
```

* Open a web interface
```sh
git instaweb
git instaweb --stop
```
```sh
git instaweb -d webrick
git instaweb -d webrick --stop
```

* Stashing, parcial save witout commit (https://youtu.be/iHJ6ZfYwEKE)
```sh
git stash
git stash list
git stash pop
git stash show stash@{0}
git diff stash@{0}
git apply stash@{0}
git stash drop stash@{0}
```

*  Shallow clones
```sh
git clone --depth 1 your_repo_url
```

*  Sync repos
```sh
# Note the period for cwd >>>>>>>>>>>>>>>>>>>>>>>> v
git clone --bare https://your-source-repo/repo.git .
git push --mirror https://your-destination-repo/repo.git
```

* Sharing tags
```sh
git push --tags
```

* List git contributos
```sh
git shortlog -s -n
```

* Git deamon
```sh
git daemon —base-path=/… —export-all
```

* Create a new repository from a path preserving the history (http://gbayer.com/development/moving-files-from-one-git-repository-to-another-preserving-history/)
```sh
git filter-branch --subdirectory-filter src/Pumukit/MoodleBundle/ -- --all
```

* Manual pull request merge

  * Step 1: From your project repository, check out a new branch and test the changes.

   ```sh
   git checkout -b ppettit-f/audio-rework master
   git pull git://github.com/ppettit/Galicaster.git f/audio-rework
   ```

  * Step 2: Merge the changes and update on GitHub.

   ```sh
   git checkout master
   git merge ppettit-f/audio-rework
   git push origin master
   ```

  * Other Manual pull request merge

  ```sh
  git clone https://github.com/teltek/Galicaster.git
  cd Galicaster
  git checkout dev_next_generation
  git checkout -b gitlab/dev_next_generation
  git pull http://gitlab.teltek.es/galicaster/galicaster.git dev_next_generation
  git checkout dev_next_generation
  git merge github/dev_next_generation
  git push origin dev_next_generation
  ```

* Force push considered harmful; understanding git's `--force-with-lease` (https://developer.atlassian.com/blog/2015/04/force-with-lease/)

```sh
git commit --force-with-lease
```

* Add all empty dirs to git touching a .gitignore file,  except the .git folder itself:
```sh
find . \( -type d -empty \) -and \( -not -regex ./\.git.* \) -exec touch {}/.gitignore \;
```

* Check ignore files
```sh
git check-ignore -v *
```


* Git remote server using SSH or file:
```sh
mkdir -p git/project1.git
cd git/project1.git
git init --bare
git clone ssh://dev@git.example.com/home/dev/git/project1.git
or
git clone file:///home/dev/git/project1.git
```


* Add line break to git commit -m from command line (http://stackoverflow.com/questions/5064563/add-line-break-to-git-commit-m-from-command-line)
```sh
git commit -m 'Message
goes
here'
```

* Show lines added, lines changed and lines removed on a commit
```sh
git show --numstat 38f1fed
```

* Cleanup unnecessary files and optimize the local repository
```sh
git gc
```

* Squash several Git commits into a single commit
fast:
```sh
# Switch to the master branch and make sure you are up to date.
git checkout master
git fetch # this may be necessary (depending on your git config) to receive updates on origin/master
git pull

# Merge the feature branch into the master branch.
git merge feature_branch

# Reset the master branch to origin's state.
git reset origin/master

# Git now considers all changes as unstaged changes.
# We can add these changes as one commit.
# Adding . will also add untracked files.
git add --all
git commit
```
or manual

```sh
git rebase -i master
```
https://makandracards.com/makandra/527-squash-several-git-commits-into-a-single-commit


gitflow
----
* http://nvie.com/posts/a-successful-git-branching-model/
* https://guides.github.com/introduction/flow/
* http://stackoverflow.com/questions/18371741/git-branching-strategy-integated-with-testing-qa-process
* https://trunkbaseddevelopment.com (alternative)


gitconfig
----
https://github.com/rubenrua/dotfiles/blob/master/.gitconfig


other
-----
* https://help.github.com/articles/remove-sensitive-data/
* https://vimeo.com/82408340
* http://ndpsoftware.com/git-cheatsheet.html