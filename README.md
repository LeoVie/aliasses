# Aliasses

## Git (.gitconfig)
```
[alias]
  st = status
  adda = add -A
  com = commit -m
```

### Use different configs for different directories
`.gitconfig`:
```
[includeIf "gitdir:~/development/company/"]
  path = .gitconfig-company
[includeIf "gitdir:~/development/private/"]
  path = .gitconfig-private
```

`.gitconfig-company`:
```
[user]
name = Name
email = name@company.com
```

`.gitconfig-private`:
```
[user]
name = Name
email = name@private.com
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
alias pst='phpstorm'
alias nproc="sysctl -n hw.physicalcpu"
follow-redirects() { wget -S --spider "$1" 2>&1  | grep -oP '^--[[:digit:]: -]{19}--  \K.*'; }
compress-pdf() { gs -sDEVICE=pdfwrite -DCompatibilityLevel=1.4 -dPDFSETTINGS=/printer -dNOPAUSE -dQUIET -dBATCH -sOutputFile="$2" "$1"; }
pdf-to-grayscale() { gs -sDEVICE=pdfwrite -dProcessColorModel=/DeviceGray -dColorConversionStrategy=/Gray -dPDFUseOldCMS=false -o "$2" -f "$1"; }

# https://localheinz.com/articles/2020/05/05/switching-between-php-versions-when-using-homebrew/
# determine versions of PHP installed with HomeBrew
installedPhpVersions=($(brew ls --versions | ggrep -E 'php(@.*)?\s' | ggrep -oP '(?<=\s)\d\.\d' | uniq | sort))

# create alias for every version of PHP installed with HomeBrew
for phpVersion in ${installedPhpVersions[*]}; do
    value="{"

    for otherPhpVersion in ${installedPhpVersions[*]}; do
        if [ "${otherPhpVersion}" = "${phpVersion}" ]; then
            continue
        fi

        # unlink other PHP version
        value="${value} brew unlink php@${otherPhpVersion};"
    done

    # link desired PHP version
    value="${value} brew link php@${phpVersion} --force --overwrite; } &> /dev/null && php -v"

    alias "${phpVersion}"="${value}"
done


installedServices=($(ls ~/development/services))
for service in ${installedServices[*]}; do
    alias "$service"="phpstorm ~/development/services/$service"
done
```
