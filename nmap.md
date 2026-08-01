# nmap

scan a host for open ports

    nmap host


scan a specific port range

    nmap -p 1-1000 host


scan the most common 100 ports quickly

    nmap -F host


detect the OS and service versions

    nmap -A host


scan an entire subnet

    nmap 192.168.1.0/24


check which hosts are up on a subnet (no port scan)

    nmap -sn 192.168.1.0/24


scan with stealth (SYN scan, requires root)

    sudo nmap -sS host


scan for UDP ports

    sudo nmap -sU -p 53,67,123 host


save output to a file

    nmap -oN scan.txt host


