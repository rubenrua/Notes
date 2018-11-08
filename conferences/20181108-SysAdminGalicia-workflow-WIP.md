# Trucos para meyorar o teu Workflow

08-11-2018

## TOOLs I love:

### Emacs
pass

### GIT
git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit

https://coderwall.com/p/v58xvw/git-lg

### Ripgrep
rg (see ag) > grep
https://beyondgrep.com/feature-comparison/

### Autojump
autojump (see fasd) > cd

---> https://remysharp.com/2018/08/23/cli-improved <----

## `BI` with linux tools:
```sh
grep XXXX data_access.log | sort | uniq -c | sort -h
cut -d " " -f 2 data_access.log | grep XXXX | sort | uniq -c | sort -h | sed 's/\s\+/ /g'
```
https://www.thegeekstuff.com/2013/06/cut-command-examples
https://github.com/dbohdan/structured-text-tools
https://www.datascienceatthecommandline.com

### Execute xargs in parallel
```sh
find src -type f -name "*.php" -print0 | xargs -0 -n1 -P8 php -l
printf %s\\n {0..99} | xargs -n 1 -P 8 script-to-run.sh input/ output/
cat commands.sh | xargs -P4  -I "{}" sh -c "{}"
```

Note: See also `parallel`.
https://stackoverflow.com/questions/28357997/running-programs-in-parallel-using-xargs
https://mike42.me/blog/how-to-use-parallel-to-speed-up-your-work



