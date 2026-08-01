# dig

look up the A record for a domain

    dig example.com


look up a specific record type

    dig example.com MX


look up the AAAA (IPv6) record

    dig example.com AAAA


reverse DNS lookup (PTR record)

    dig -x 8.8.8.8


query a specific DNS server

    dig @8.8.8.8 example.com


short output (just the answer)

    dig +short example.com


trace the full DNS resolution path

    dig +trace example.com


look up all record types

    dig example.com ANY


check NS (nameserver) records

    dig example.com NS


check CNAME records

    dig www.example.com CNAME


