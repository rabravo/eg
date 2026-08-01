# jq

pretty-print a JSON file

    jq . file.json


extract a top-level field

    jq '.name' file.json


extract a nested field

    jq '.user.email' file.json


extract all elements of an array

    jq '.items[]' file.json


filter array elements by a condition

    jq '.items[] | select(.active == true)' file.json


extract a field from each array element

    jq '.items[].name' file.json


compact output (no pretty printing)

    jq -c '.' file.json


use with curl to parse API responses

    curl -s https://api.example.com/data | jq '.results[]'


