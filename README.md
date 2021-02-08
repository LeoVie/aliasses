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
export PYTHONIOENCODING="utf-8"
alias mergepdf='qpdf --empty --pages [0-9][0-9]_*.pdf -- '
```
