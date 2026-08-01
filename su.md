# su

switch to the root user (prompts for root's password)

    su

    # su          substitute user — starts a new shell as another user
    # (no arg)    defaults to root


switch to a specific user

    su abravo

    # abravo      the target username; prompts for that user's password


start a login shell as root (loads root's full environment)

    su -

    # -           equivalent to --login; sources root's profile (~/.bashrc, ~/.profile, etc.)
    # without -   inherits the current environment (PATH, HOME, etc. stay as the caller's)


start a login shell as a specific user

    su - abravo

    # combines target user with --login to get a clean environment for that user


run a single command as another user without opening a shell

    su -c "whoami" abravo

    # -c "cmd"    execute cmd in a subshell, then return to the current session
