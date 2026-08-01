# bg

resume the most recent stopped job in the background

    bg


resume a specific stopped job in the background by job number

    bg %1


resume multiple stopped jobs in the background at once

    bg %1 %2 %3


suspend a foreground job, then resume it in the background

    Ctrl+Z
    bg


start a command in the background from the start (preferred over bg)

    some_command &


list background jobs to check status

    jobs -r


bring a background job back to the foreground

    fg %1


wait for all background jobs to finish before continuing

    wait


wait for a specific background job to finish

    wait %1


