BASH
====


Tips
----

```bash
man bash

# import a file
. locallib.sh
source locallib.sh

#set
set -e #exit on error
set -u #exit when a variable is unset
set -x #print out every command it runs before running it
help set

#http://stackoverflow.com/questions/59895/getting-the-source-directory-of-a-bash-script-from-within
DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"

#https://stackoverflow.com/questions/5947742/how-to-change-the-output-color-of-echo-in-linux
for (( i = 30; i <= 37; i++ ));
do echo -e "\e[0;"$i"m  Hi stackoverflow\e[0m";
done

#https://misc.flogisoft.com/bash/tip_colors_and_formatting
RESET='\033[0m'
BOLD='\033[1m'
BLACK='\033[38;5;0m'
RED='\033[38;5;1m'
GREEN='\033[38;5;2m'

echo -e "${BOLD}Hello world${RESET}"

```

Links
-----

* http://jvns.ca/blog/2017/03/26/bash-quirks/ (https://twitter.com/b0rk/status/846203979403083776)
* https://www.shellcheck.net/
* https://eklitzke.org/bash-$%2A-and-$@ from https://news.ycombinator.com/item?id=22027809
* https://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_06_02