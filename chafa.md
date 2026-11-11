# chafa

display an image using the Kitty graphics protocol (Ghostty, requires herdr kitty_graphics enabled)

    chafa --format kitty image.png


display an image using Sixel (not supported by herdr; works in plain Ghostty pane)

    chafa --format sixel image.png


display an image using iTerm2 inline protocol

    chafa --format iterm image.png


display an image as Unicode symbols (works everywhere, no graphics protocol needed)

    chafa --format symbols image.png


fix broken libjxl dylib after a jpeg-xl upgrade (chafa crashes with dyld error)

    brew reinstall chafa

    # chafa links against the exact libjxl minor version; reinstalling relinks against the installed one


# Notes
# - Inside herdr on Ghostty: use --format kitty (sixel is not passed through)
# - herdr requires terminal.kitty_graphics = true in its config; check with:
#     herdr --default-config | grep -i kitty
# - kitty_graphics requires a full server restart to take effect (reload-config is not enough):
#     herdr server stop && herdr
# - Running herdr inside tmux drops kitty graphics (tmux does not pass them through)
