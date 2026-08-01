# gosu

run a command as a specific user (Docker-friendly su/sudo replacement)

    gosu abravo bash

    # gosu        lightweight su for containers — drops privileges cleanly and execs the command
    # abravo      target user (name or UID); can also be "user:group" (e.g. abravo:students)
    # bash        command to run as that user; becomes PID 1 (no wrapper shell stays around)


run a one-off command as another user inside a container

    gosu www-data php artisan migrate

    # www-data    the user the web server runs as (common in PHP/Apache containers)
    # unlike sudo, gosu does not require a password or sudoers configuration


use as a Docker ENTRYPOINT to drop from root to a service user

    # in a Dockerfile or entrypoint.sh:
    exec gosu appuser "$@"

    # exec        replaces the shell with gosu so signals (SIGTERM, etc.) reach the process
    # appuser     unprivileged user created earlier in the Dockerfile (RUN useradd appuser)
    # "$@"        forwards all arguments passed to the entrypoint


why gosu instead of su or sudo inside containers?

    # su    spawns a login shell wrapper — signals don't reach the child process cleanly
    # sudo  requires sudoers config and adds overhead; not always installed in minimal images
    # gosu  does a direct exec() — no wrapper, no TTY needed, PID stays clean
