# jobs

list active jobs in the current shell session

    jobs


list jobs with process IDs

    jobs -l


list process IDs only

    jobs -p


list only running jobs

    jobs -r


list only stopped jobs

    jobs -s


list only jobs whose status changed since last notification

    jobs -n


show status of a specific job by job number

    jobs %1


resume a stopped job in the background

    bg %1


bring a background job to the foreground

    fg %1


send a job to the background (append & when starting)

    some_command &


wait for all background jobs to finish

    wait


kill a job by job spec

    kill %1


