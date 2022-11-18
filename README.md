# Aliasses

## Git (.gitconfig)
```
[alias]
  st = status
  adda = add -A
  com = commit -m
```

## Bash (.bashrc)
```
alias compi='composer install --prefer-source'
alias compu='composer update --prefer-source'
alias compr='composer require --prefer-source'
alias cd..2='cd ../..'
alias cd..3='cd ../../..'
alias cd..4='cd ../../../..'
alias git-recursive-clean='git clean -xffd && git submodule foreach --recursive git clean -xffd'
alias mergepdf='qpdf --empty --pages [0-9][0-9]_*.pdf -- '
alias dcu='docker-compose up -d'
alias dcd='docker-compose down'
alias dcr='dcd && dcu'
alias bytesize='stat --format="%s" '
alias phpversion='sudo update-alternatives --config php'
alias exp='explorer.exe .'
alias ta='XDEBUG_MODE=coverage composer testall'
alias xdebug-on='sudo phpenmod xdebug'
alias xdebug-off='sudo phpdismod xdebug'
alias gitssh='eval "$(ssh-agent -s)" && ssh-add ~/.ssh/private_openssh.ppk'
alias comt='~/scripts/commit-with-ticket.sh'
alias ta='XDEBUG_MODE=coverage composer testall'
alias t='XDEBUG_MODE=coverage composer phpunit'
alias pull-in-dir='ls -d */ | xargs -I{} git -C {} pull'
follow-redirects() { wget -S --spider "$1" 2>&1  | grep -oP '^--[[:digit:]: -]{19}--  \K.*'; }
```
