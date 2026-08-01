# srun

request an interactive shell with 1 node, 8 CPUs, 1 GPU, for 1 hour

    srun -N 1 -c 8 -t 1:00:00 --gres=gpu:1 --pty /bin/bash --login


show all jobs currently running or allocated to you

    squeue -u $USER


show detailed info on your allocated jobs (nodes, CPUs, GPUs, time left)

    squeue -u $USER -o "%.10i %.9P %.20j %.8T %.10M %.10L %.6D %.6C %.b %R"


show which nodes are allocated to a specific job

    squeue -u $USER -o "%.10i %N"


check resource usage of a running job by job ID

    sstat --jobs=<jobid> --format=JobID,AveCPU,AveRSS,AveVMSize


show GPU allocation details for your running jobs

    squeue -u $USER -o "%.10i %.9P %.20j %.8T %.6C %.b"


request an interactive session with no GPU

    srun -N 1 -c 4 -t 0:30:00 --pty /bin/bash --login


request a job on a specific partition

    srun -N 1 -c 8 -t 2:00:00 --partition=gpu --gres=gpu:1 --pty /bin/bash --login


run a single command non-interactively (no pseudo-terminal)

    srun -N 1 -c 4 -t 0:10:00 python script.py
