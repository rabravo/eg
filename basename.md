# basename

get the filename from a full path

    basename $(which man)


strip a specific extension

    basename file.tar.gz .tar.gz


get filename without extension in a bash script

    fileNoExtension="${jpgFile%.*}"


get just the extension in a bash script

    fileExtension="${jpgFile##*.}"


