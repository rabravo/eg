# tr

convert lowercase to uppercase

    echo "hello world" | tr 'a-z' 'A-Z'


delete specific characters

    echo "hello 123" | tr -d '0-9'


squeeze repeated characters into one

    echo "aaa   bbb" | tr -s ' '


replace colons with newlines

    echo "$PATH" | tr ':' '\n'


remove newlines

    cat file.txt | tr -d '\n'


