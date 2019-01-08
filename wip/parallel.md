* https://www.gnu.org/software/parallel/parallel_tutorial.html
* https://www.gnu.org/software/parallel/parallel_alternatives.html
* https://www.msi.umn.edu/support/faq/how-can-i-use-gnu-parallel-run-lot-commands-parallel

mkfifo fifo
tail  -f fifo | parallel

# https://www.gnu.org/software/parallel/parallel_tutorial.html#Number-of-simultaneous-jobs
# -j Number of simultaneous jobs
# --jobs 0 will run as many jobs in parallel as possible:

# https://www.gnu.org/software/parallel/parallel_tutorial.html#CSV-as-SQL-base
#  DBURL=sqlite3:///%2Ftmp%2Fmydatabase
#  DBURLTABLE=$DBURL/mytable
#  parallel --sqlandworker $DBURLTABLE echo ::: foo bar ::: baz quuz
