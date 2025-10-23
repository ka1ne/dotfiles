# dotfiles


## clean start TMUX on start
```
if command -v tmux &> /dev/null && [ -n "$PS1" ] && [[ ! "$TERM" =~ screen ]] && [[ ! "$TERM" =~ tmux ]] && [ -z "$TMUX" ]; then
    exec tmux new-session -A -s main
fi
```

## Git branch on prompt
```
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/[\1]/'
}

# Set the prompt with direct color codes
PS1='\W \[\033[0;36m\]$(parse_git_branch)\[\033[0m\] $ '
```

## pbcopy > windows clipboard for wsl
```
alias pbcopy='clip.exe'
alias pbpaste='powershell.exe Get-Clipboard'
```
