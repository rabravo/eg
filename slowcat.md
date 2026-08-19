# slowcat

print a file slowly, one character at a time (useful for demos and screencasts)

    slowcat file.txt


set delay between characters (in seconds, fractions allowed)

    slowcat -d 0.05 file.txt


set delay between lines instead of characters

    slowcat -l 0.5 file.txt


pipe output from another command through slowcat

    echo "Deploying to production..." | slowcat -d 0.03


simulate a slow terminal session for a live demo

    slowcat -d 0.02 demo_script.sh


chain with lolcat for colorized slow output

    slowcat -d 0.04 ascii_art.txt | lolcat


replay a saved terminal session slowly

    cat session.txt | slowcat -d 0.01


