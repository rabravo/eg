# read

read a line from stdin into a variable

    read line


prompt the user and read their input

    read -p "Enter your name: " name


read a password without echoing input to the terminal

    read -s -p "Password: " password


read into the default REPLY variable (no name given)

    read
    echo "$REPLY"


split a line into multiple variables

    read first last <<< "Jane Doe"


read without interpreting backslash escapes (recommended for file input)

    read -r line


read a file line by line

    while IFS= read -r line; do
        echo "$line"
    done < file.txt


read words into an array

    read -a words <<< "one two three"
    echo "${words[0]}"   # one


time out if no input after N seconds

    read -t 5 -p "Enter input (5s timeout): " response


read exactly N characters (no newline needed)

    read -n 1 -p "Press any key to continue..." key


read until a custom delimiter instead of newline

    read -d ':' field <<< "foo:bar"


read from a file descriptor

    read -u 3 line 3< file.txt


pre-fill input with default text (readline mode)

    read -e -i "default value" -p "Edit or accept: " input


confirm a yes/no prompt

    read -r -p "Continue? [y/N] " confirm
    [[ "$confirm" == [yY] ]] && echo "proceeding" || echo "aborted"


