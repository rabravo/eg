# fg

bring the most recent background or stopped job to the foreground

    fg


bring a specific job to the foreground by job number

    fg %1


bring a job to the foreground by name (prefix match)

    fg %python


bring a job to the foreground by name (substring match)

    fg %?server


list jobs first, then foreground one

    jobs
    fg %2


suspend a foreground job (send to stopped state)

    Ctrl+Z


resume a stopped job in the foreground

    Ctrl+Z
    fg


resume a stopped job in the background instead

    Ctrl+Z
    bg %1


