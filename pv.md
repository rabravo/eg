# pv

monitor progress of data through a pipe (pipe viewer)

    pv file.tar.gz | gzip -d > file.tar


show progress while copying a file

    pv input.iso > output.iso


set the expected size so pv can show a progress bar and ETA

    pv -s 2G input.tar | gzip > input.tar.gz


limit transfer rate to 1 MB/s

    pv -L 1m input.img > output.img


monitor dd progress (insert pv between source and destination)

    dd if=/dev/sda | pv -s 500G | dd of=/dev/sdb


display throughput in bytes per second, suppress progress bar

    pv -f file.log | wc -l

  -f forces output to stderr so it doesn't corrupt a piped byte stream.


show line count progress instead of bytes (-l counts newlines)

    pv -l largefile.csv | awk -F, '{print $2}'


quiet mode: suppress bar, print final summary to stderr on exit

    pv -q -F "%b transferred in %T at %a avg" bigfile.bin > /dev/null


watch a running process's file descriptor (Linux only)

    pv -d PID:FD


