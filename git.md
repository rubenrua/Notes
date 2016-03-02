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
```
[alias]
    lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

 * `Add` and `commit` together.
```sh
git commit -a -m 'msg'
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

