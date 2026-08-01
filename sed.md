# sed

replace first occurrence of a pattern in a file (in-place, Linux)

    sed -i 's/pattern/replacement/' filename


replace all occurrences of a pattern in a file (in-place, Linux)

    sed -i 's/pattern/replacement/g' filename


replace all occurrences (in-place, macOS)

    sed -i '' 's/pattern/replacement/g' filename


replace only the first occurrence

    sed '0,/pattern/s/pattern/replacement/' filename


dry run — print result without changing the file

    sed 's/pattern/replacement/g' filename


use a different delimiter (useful when pattern contains slashes)

    sed -i 's|path/old|path/new|g' filename


