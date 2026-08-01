# vim

open a file at a specific line number

    vim +42 somefile


# Tabs

open a new tab

    :tabnew


close current tab

    :tabc


close all tabs except current

    :tabo


close the Nth tab

    :Ntabc



# Show Invisible Characters

show tabs, line endings, carriage returns

    :set list


hide them again

    :set nolist


customize what symbols are shown

    :set listchars=tab:>·,trail:·,extends:↷,precedes:↶,eol:$



# Line Endings

check if file uses DOS line endings

    :set fileformat


convert DOS line endings to Unix

    :set fileformat=unix
    :w



# Troubleshooting

if vim freezes (accidentally hit Ctrl+S), unfreeze with

    Ctrl+Q


