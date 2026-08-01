# nc

test if a TCP port is open on a host

    nc -zv host 443


scan a range of ports

    nc -zv host 20-80


send a message to a listening server

    echo "hello" | nc host 1234


start a simple listening server on port 1234

    nc -l 1234


transfer a file from one host to another (receiver first)

    nc -l 9999 > received_file.tar.gz


then on the sender

    cat file.tar.gz | nc receiver_host 9999


create a simple chat between two machines (listener)

    nc -l 5000


connect from the other machine

    nc host 5000


send an HTTP request manually

    echo -e "GET / HTTP/1.0\r\n\r\n" | nc example.com 80


