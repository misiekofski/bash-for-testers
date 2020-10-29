We can create .bashrc file in ~/ directory (c:/Users/username or /home/username)

First we can add aliases (shortcuts to more commands)

```bash
alias clone='git clone'
alias gc='git commit -m'
alias gd='git difftool -y -x "sdiff" | less'
```

or more advanced 'scripts':

```bash
alias getrepos='ls | xargs -I{} git -C {} pull'
alias showbranches='for dir in $(ls -d */);do (cd $dir && echo "$dir [$(git rev-parse --abbrev-ref HEAD)]") ; done'
```

or even functions:

```bash
cssmin() {
    sed "s@/\*.*\*/@@g" $1 | sed "/\/\*/,/\*\//d" | sed -e 's/^[ \t]*//g; s/[ \t]*$//g; s/\([:{;,]\) /\1/g; s/ {/{/g; s/\/\*.*\*\///g; /^$/d' | sed -e :a -e '$!N; s/\n\(.\)/\1/; ta' > $2
}
```