# bash_customizations
A place to store all the customizations for BASH

## Mac

### `.bash-profile`

```
source /usr/local/git/contrib/completion/git-completion.bash
GIT_PS1_SHOWDIRTYSTATE=true
#export PS1='[\u@mbp \w$(__git_ps1)]\$ '
source ~/.git-prompt.sh
#export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\] (parse_git_branch)\[\033[00m\] \$"
parse_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\u@\h \[\033[32m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\] $ "
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
alias ls='ls -GFh'
alias gdm='git branch --merged | egrep -v "(^\*|master|dev|RC)" | xargs git branch -d'
```

### Delete all merged branches

* `git branch --merged | egrep -v "(^\*|master|dev|RC)" | xargs git branch -d`
