# printf

print a string without a trailing newline

    printf "hello"


print a string with a newline

    printf "hello\n"


print multiple values with a format string

    printf "Name: %s, Age: %d\n" "Alice" 30


pad a string to a fixed width (right-aligned)

    printf "%10s\n" "hello"


pad a string left-aligned

    printf "%-10s|\n" "hello"


print a number with leading zeros

    printf "%05d\n" 42


print a floating point number with fixed decimal places

    printf "%.2f\n" 3.14159


print in hexadecimal, octal, and scientific notation

    printf "%x %o %e\n" 255 255 12345.6789


repeat a format for multiple arguments

    printf "%s\n" one two three


quote a value safely for reuse as shell input

    printf "%q\n" "hello world; rm -rf /"


print a date/time string using strftime format

    printf "%(%Y-%m-%d %H:%M:%S)T\n" -1


capture output into a variable instead of printing

    printf -v result "%-10s %d" "score" 42
    echo "$result"


print a separator line of repeated characters

    printf '%0.s-' {1..40}; printf '\n'


print a table with aligned columns

    printf "%-15s %5s %8s\n" "Name" "Age" "Score"
    printf "%-15s %5d %8.2f\n" "Alice" 30 99.5
    printf "%-15s %5d %8.2f\n" "Bob" 25 87.33


print to stderr

    printf "error: %s\n" "something went wrong" >&2


