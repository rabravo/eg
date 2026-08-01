# xargs

delete all .log files found by find

    find . -name "*.log" | xargs rm


run a command on each item, one at a time

    cat list.txt | xargs -I {} echo "Processing: {}"


run commands in parallel (4 at a time)

    cat urls.txt | xargs -P 4 -I {} curl -O {}


pass multiple arguments per command invocation

    echo "a b c" | xargs mkdir


handle filenames with spaces (use null delimiter)

    find . -name "*.txt" -print0 | xargs -0 grep "pattern"


