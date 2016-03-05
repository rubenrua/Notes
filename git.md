GIT
===

TUTORIALES:
-----------

* http://git-scm.com/documentation (official)
* http://learn.github.com/ (basic Code School)
* http://try.github.com/ (basic GitHub)
* https://www.atlassian.com/git/tutorials/advanced-overview (advanced)
* http://pcottle.github.io/learnGitBranching/ (advanced)
* http://byte.kde.org/~zrusin/git/git-cheat-sheet.svg (cheat-sheet)
* https://github.com/tiimgreen/github-cheat-sheet (cheat-sheet src)
* http://aprendegit.com (blog)


Tips
----
* Pretty log
```sh
git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

* Git alias. Add in `~/.gitconfig`
```ini
[alias]
    lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

* `Add` and `commit` together.
```sh
git commit -a -m 'msg'
```

* Merge witout commit (no check in prod):
```sh
git merge --no-commit <branch>
git merge --abort
```

* List branches ordered by most recent commit.
```sh
git for-each-ref --sort=-committerdate refs/remotes
```

* Reset working directory
```sh
git clean -xdf
```

* Create a new branch
```sh
git checkout -b branch_name
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

* Delete remote branch or remote tag
```sh
git push origin :branch-to-delete
git push origin --delete branch-to-delete (git >= 1.7)
```

* Sharing tags
```sh
git push --tags
```

* Delete commits from the remote repo using other branch (https://youtu.be/mdZvYyIKURo)
```sh
git branch -D master
git push origin :master  #Cambiar el HEAD antes via web en github
git checkout -b master
git push origin master
```

* List git contributos
```sh
git shortlog -s -n
```

* Git deamon
```sh
git daemon —base-path=/… —export-all
```
