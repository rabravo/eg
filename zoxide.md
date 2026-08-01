# zoxide

jump to the highest-ranked directory matching a query

    z foo


jump interactively using fzf (requires fzf)

    zi foo


jump to an exact path (bypasses ranking)

    z ~/projects/my-repo


add a directory to the database manually

    zoxide add /path/to/dir


list all directories in the database with their scores

    zoxide query --list --score


query the best match without jumping (prints the path)

    zoxide query foo


remove a directory from the database

    zoxide remove /path/to/dir


remove stale entries (directories that no longer exist)

    zoxide edit --delete $(zoxide query --list | awk '{print $2}' | while read p; do [ -d "$p" ] || echo "$p"; done)


import history from z / autojump / fasd

    zoxide import --from z ~/.z
    zoxide import --from autojump ~/.local/share/autojump/autojump.txt


print the current database path

    echo $ZOXIDE_DATA


# Shell Integration

add to ~/.bashrc or ~/.zshrc to initialise zoxide

    eval "$(zoxide init bash)"      # bash
    eval "$(zoxide init zsh)"       # zsh
    zoxide init fish | source       # fish


alias z and zi come from the init; override the command name

    eval "$(zoxide init bash --cmd j)"   # uses j / ji instead of z / zi
