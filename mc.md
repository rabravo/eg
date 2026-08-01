# mc (Midnight Commander)

open mc in current directory

    mc

open with a remote SFTP server in the right panel

    mc sftp://user@host

open with a specific remote path

    mc sftp://user@host/var/www/html/

## panels

    Tab             switch between left and right panel
    Alt+i           sync inactive panel to active panel's directory
    Alt+o           open selected dir in opposite panel
    Ctrl+u          swap panels

## navigation

    Arrow keys      move cursor
    Enter           open file or enter directory
    Backspace       go up one directory
    Ctrl+r          refresh panel

## file operations

    F5              copy selected file/dir to opposite panel
    F6              move selected file/dir to opposite panel
    F7              create new directory
    F8              delete selected file/dir
    F4              edit file
    F3              view file

## selecting files

    Insert          select/deselect file under cursor
    +               select files by pattern (e.g. *.html)
    \               deselect files by pattern
    *               invert selection

## menus and search

    F9              open menu bar
    F10             quit
    Alt+s           quick search (type to jump to filename)
    Ctrl+s          search as you type

## macOS / terminal F-key fallbacks (if F-keys are intercepted)

    Esc 3           F3 (view)
    Esc 4           F4 (edit)
    Esc 5           F5 (copy)
    Esc 6           F6 (move)
    Esc 7           F7 (mkdir)
    Esc 8           F8 (delete)
    Esc 9           F9 (menu)
    Esc 0           F10 (quit)
