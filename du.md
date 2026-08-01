# du

show disk usage of the current directory

    du -sh .


show disk usage of each subdirectory

    du -sh */


show disk usage sorted by size (largest first)

    du -sh * | sort -rh


show disk usage up to 2 levels deep

    du -h --max-depth=2 .


find the 10 largest directories under /

    du -h / 2>/dev/null | sort -rh | head -10


