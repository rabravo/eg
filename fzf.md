# fzf

fuzzy-find a file and open it in vim

    vim $(fzf)


fuzzy-search command history and execute the selection

    history | fzf | bash


fuzzy-find and cd into a directory

    cd $(find . -type d | fzf)


preview file contents while browsing

    fzf --preview 'cat {}'


fuzzy-search git branches and check one out

    git checkout $(git branch | fzf)


pipe any list into fzf for interactive selection

    cat list.txt | fzf


filter output and pass selection to another command

    ps aux | fzf | awk '{print $2}' | xargs kill


