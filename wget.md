# wget

download a file from a URL

    wget https://example.com/file.zip


download only specific file extensions

    wget --accept ext URL


download while rejecting specific file extensions

    wget --reject ext URL


resume an interrupted download

    wget -c https://example.com/file.zip


