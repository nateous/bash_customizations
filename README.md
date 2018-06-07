# bash_customizations
A place to store all the customizations for BASH

### Delete all merged branches

* `git branch --merged | egrep -v "(^\*|master|dev|RC)" | xargs git branch -d`
