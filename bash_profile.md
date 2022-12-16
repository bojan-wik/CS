#tools 

.bash_profile
```bash
# Ignore duplicates in command history and increase history size to 1000 lines
export HISTCONTROL=ignoredumps
export HISTSIZE=1000

# Listing aliases
alias ls='ls -F --color=auto --show-control-chars'
alias ll='ls -laXh'

# Grep aliases
alias grep='grep --color=auto'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'

# File manipulation --interactive --verbose
alias rm='rm -iv'
alias mv='mv -iv'
alias cp='cp -iv'
alias gzip='gzip -v'

# Other
alias diff='diff --color'

# Pimp my prompt
PS1="\[\033[0;32m\]\u@\h \[\033[0;33m\]\w\[\033[0m\] $ "
export PS1
```

Plik .bash_profile nie jest tworzony defaultowo. Trzeba go stworzyć i umieścić w home directory tzn. `~/.bash_profile`