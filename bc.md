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


convert decimal to binary

    echo "obase=2; 42" | bc


define and call a function (factorial)

    echo "define f(n) { if (n <= 1) return 1; return n * f(n-1) }; f(10)" | bc


compute square root

    echo "scale=10; sqrt(2)" | bc -l


compute natural log

    echo "scale=10; l(100)" | bc -l


compute power

    echo "scale=5; e(3)" | bc -l


math library functions (-l)

    s(x)    sine of x (radians)        echo "scale=10; s(1)" | bc -l
    c(x)    cosine of x (radians)      echo "scale=10; c(1)" | bc -l
    a(x)    arctangent of x            echo "scale=10; a(1)*4" | bc -l   # pi
    l(x)    natural logarithm of x     echo "scale=10; l(1)" | bc -l
    e(x)    e raised to the power x    echo "scale=10; e(1)" | bc -l
    j(n,x)  Bessel function of x       echo "scale=10; j(0,1)" | bc -l
    sqrt(x) square root of x           echo "scale=10; sqrt(9)" | bc -l


built-in functions (no -l needed)

    length(x)   total number of significant digits    echo "length(123.456)" | bc
    scale(x)    number of digits after decimal        echo "scale(3.14159)" | bc
    read()      read a number interactively            bc <<< "x = read(); x * 2"


user-defined functions

    absolute value

        echo "define abs(x) { if (x < 0) return -x; return x }; abs(-42)" | bc

    power (integer exponent)

        echo "define pow(b,n) { auto r; r=1; while(n>0){r*=b; n-=1}; return r }; pow(2,10)" | bc

    fibonacci

        echo "define fib(n) { if (n<=1) return n; return fib(n-1)+fib(n-2) }; fib(10)" | bc

    greatest common divisor

        echo "define gcd(a,b) { if (b==0) return a; return gcd(b, a%b) }; gcd(48,18)" | bc

    celsius to fahrenheit

        echo "define ctof(c) { return c * 9/5 + 32 }; ctof(100)" | bc

    fahrenheit to celsius

        echo "define ftoc(f) { return (f - 32) * 5/9 }; ftoc(212)" | bc


