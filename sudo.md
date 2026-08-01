# sudo

run a command as root (prompts for your own password)

    sudo apt update

    # sudo        superuser do — runs the next command with elevated privileges
    # uses YOUR password (not root's), and only if your account is in the sudoers list


run a command as a specific user

    sudo -u abravo whoami

    # -u abravo   run as the user abravo instead of root


open an interactive root shell

    sudo -i

    # -i          login shell as root — loads root's full environment (PATH, HOME, etc.)


open an interactive root shell (inherits current environment)

    sudo -s

    # -s          shell as root but keeps the caller's environment variables


run a command as root without a password prompt (if NOPASSWD is set in sudoers)

    sudo systemctl restart nginx

    # works without a password only when the sudoers file grants NOPASSWD for the command


list the commands the current user is allowed to run with sudo

    sudo -l

    # -l          list allowed (and forbidden) commands per the sudoers policy
