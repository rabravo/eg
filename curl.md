# curl

fetch a URL and print the response

    curl https://example.com


save response to a file

    curl -o output.html https://example.com


follow redirects

    curl -L https://example.com


send a POST request with JSON body

    curl -X POST -H "Content-Type: application/json" \
        -d '{"key":"value"}' https://api.example.com/endpoint


add a request header

    curl -H "Authorization: Bearer TOKEN" https://api.example.com


show response headers only

    curl -I https://example.com


download a file, preserving the remote filename

    curl -O https://example.com/file.tar.gz


send a form POST

    curl -X POST -F "field=value" https://example.com/form


