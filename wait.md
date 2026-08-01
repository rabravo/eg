# wait

wait for all background jobs in the current shell to finish

    wait


wait for a specific background job by PID

    wait 1234


wait for a specific job by job spec

    wait %1


wait for multiple PIDs

    wait 1234 5678


capture the exit status of a background job

    some_command &
    pid=$!
    wait $pid
    echo "exited with $?"


run jobs in parallel, then wait for all to finish

    job1 &
    job2 &
    job3 &
    wait


wait for the next job to finish (whichever completes first)

    wait -n


wait for the next job and capture which PID finished

    wait -n -p finished_pid
    echo "job $finished_pid finished first"


wait for a process to terminate even if stopped (not just status change)

    wait -f 1234


wait for all background jobs and exit with failure if any failed

    job1 &
    job2 &
    wait && echo "all succeeded" || echo "at least one failed"


