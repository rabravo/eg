# yazi

open yazi in current directory

    yazi

open at a specific path

    yazi /path/to/dir

open and change shell directory on exit (add to .bashrc/.zshrc)

    function y() {
        local tmp="$(mktemp -t yazi-cwd)"
        yazi "$@" --cwd-file="$tmp"
        if cwd="$(< "$tmp")" && [ -n "$cwd" ] && [ "$cwd" != "$PWD" ]; then
            cd "$cwd"
        fi
        rm -f "$tmp"
    }

## navigation

    h / ArrowLeft     go to parent directory
    l / ArrowRight    enter directory or open file
    j / ArrowDown     move cursor down
    k / ArrowUp       move cursor up
    g g               go to top of list
    G                 go to bottom of list
    ~                 go to home directory
    .                 toggle hidden files

## file operations

    Space             select/deselect file
    y                 yank (copy) selected
    d                 cut selected
    p                 paste
    D                 delete selected (move to trash)
    r                 rename file
    a                 create new file
    A                 create new directory (add / at end of name)
    o                 open with default app
    e                 open with $EDITOR

## tabs

    t                 new tab
    [                 switch to previous tab
    ]                 switch to next tab
    q                 close tab / quit if last tab

## search and filter

    /                 search filenames
    f                 filter list by pattern
    n                 jump to next search match
    N                 jump to previous search match
    z                 jump with zoxide (if installed)

## misc

    ?                 show keybindings help
    :                 open command palette
