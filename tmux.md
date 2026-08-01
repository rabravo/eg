# tmux

start a new session

    tmux


start a named session

    tmux new -s mysession


attach to the most recent session

    tmux attach


attach to a named session

    tmux attach -t mysession


list all sessions

    tmux ls


detach from the current session (keeps it running)

    Ctrl-b d


kill a named session

    tmux kill-session -t mysession



# Windows and Panes

create a new window

    Ctrl-b c


switch to the next window

    Ctrl-b n


split the pane vertically (side by side)

    Ctrl-b %


split the pane horizontally (top and bottom)

    Ctrl-b "


move between panes

    Ctrl-b arrow-key


zoom in on a pane (toggle)

    Ctrl-b z


rename the current window

    Ctrl-b ,


close the current pane

    exit


