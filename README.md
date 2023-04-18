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

### Case insensitive tab autocomplete! (current user)

```
# If ~/.inputrc doesn't exist yet: First include the original /etc/inputrc
# so it won't get overriden
if [ ! -a ~/.inputrc ]; then echo '$include /etc/inputrc' > ~/.inputrc; fi

# Add shell-option to ~/.inputrc to enable case-insensitive tab completion
echo 'set completion-ignore-case On' >> ~/.inputrc
```

#### System-wide

```
# add option to /etc/inputrc to enable case-insensitive tab completion for all users
echo 'set completion-ignore-case On' >> /etc/inputrc
# you may have to use this instead if you are not a superuser:
echo 'set completion-ignore-case On' | sudo tee -a /etc/inputrc
```

see: https://askubuntu.com/a/87066

### `.zshrc`

```
alias gdm="git branch --merged | grep -v '\*' | xargs git branch -d"
alias cleanup="git stash; git checkout main; git pull -p; gdm; function _newbranch() { if [[ \$# -eq 1 ]]; then git checkout -b \$1; fi; }; _newbranch"
```

