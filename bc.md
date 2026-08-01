# bc

open interactive calculator with math library

    bc -l


compute pi to 5000 decimal places

    echo "scale=5000; 4*a(1)" | bc -l -q


add two numbers from a script

    echo "3.14 + 2.72" | bc


convert decimal to hex

    echo "obase=16; 255" | bc


convert hex to decimal

    echo "ibase=16; FF" | bc


increase a value by 2

    echo "25.2 + 2" | bc


