# tail

print the last 10 lines of a file

    tail file.txt


print the last N lines

    tail -n 20 file.txt


follow a file as it grows (useful for logs)

    tail -f /var/log/syslog


follow multiple files at once

    tail -f app.log error.log


print all lines starting from line N

    tail -n +5 file.txt


