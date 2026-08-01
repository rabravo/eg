# set

print all shell variables and their values

    set


strict mode: exit on error, treat unset vars as errors, and catch pipeline failures

    set -euo pipefail


exit immediately if any command fails

    set -e


treat unset variables as an error instead of expanding to empty string

    set -u


make pipeline exit status reflect the first failed command, not the last

    set -o pipefail


print each command before executing it (debug/trace mode)

    set -x


turn off debug trace

    set +x


enable and disable options within a script

    set -x          # turn on
    some_command
    set +x          # turn off


print shell input lines as they are read

    set -v


disable globbing (filename expansion)

    set -f


re-enable globbing

    set +f


prevent output redirection from overwriting existing files

    set -C


check what options are currently active

    echo $-


print current option settings in reusable form

    set +o


set positional parameters ($1, $2, ...)

    set -- foo bar baz
    echo $1   # foo
    echo $2   # bar


clear all positional parameters

    set --


make all new variables automatically exported to child processes

    set -a


