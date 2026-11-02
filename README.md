# Aliasses

## Git (.gitconfig)
```gitconfig
[alias]
  st = status
  adda = add -A
  com = commit -m
```

### Use different configs for different directories
`.gitconfig`:
```gitconfig
[includeIf "gitdir:~/development/company/"]
  path = .gitconfig-company
[includeIf "gitdir:~/development/private/"]
  path = .gitconfig-private
```

`.gitconfig-company`:
```gitconfig
[user]
name = Name
email = name@company.com
```

`.gitconfig-private`:
```gitconfig
[user]
name = Name
email = name@private.com
```

## zsh (.zshrc)
```zsh
alias compi='composer install --prefer-source'
alias compu='composer update --prefer-source'
alias compr='composer require --prefer-source'
alias cd..2='cd ../..'
alias cd..3='cd ../../..'
alias cd..4='cd ../../../..'
alias dcu='docker-compose up -d'
alias dcd='docker-compose down'
alias dcr='dcd && dcu'
alias bytesize='stat --format="%s" '
alias pst='phpstorm'
alias nproc="sysctl -n hw.physicalcpu"
follow-redirects() { wget -S --spider "$1" 2>&1  | grep -oP '^--[[:digit:]: -]{19}--  \K.*'; }
alias mergepdf='qpdf --empty --pages [0-9][0-9]_*.pdf -- '
alias flushdnscache="sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder"
compress-pdf() { gs -sDEVICE=pdfwrite -DCompatibilityLevel=1.4 -dPDFSETTINGS=/printer -dNOPAUSE -dQUIET -dBATCH -sOutputFile="$2" "$1"; }
pdf-to-grayscale() { gs -sDEVICE=pdfwrite -dProcessColorModel=/DeviceGray -dColorConversionStrategy=/Gray -dPDFUseOldCMS=false -o "$2" -f "$1"; }
rebaseonto() {
  git checkout $1;
  git pull;
  git checkout -;
  git rebase --interactive $1;
}
```
