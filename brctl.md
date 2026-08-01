# brctl -- Bird Control: manage iCloud Drive sync (macOS)

## Show live iCloud sync log

    brctl log --wait --shorten

## Stream log with a filter

    brctl log --wait --shorten --predicate 'message contains "error"'

## Force download a file from iCloud to local storage

    brctl download ~/Library/Mobile\ Documents/file.pdf

## Evict a file (remove local copy, keep in iCloud)

    brctl evict ~/Library/Mobile\ Documents/file.pdf

## Monitor sync activity for all containers

    brctl monitor

## Monitor a specific CloudKit container

    brctl monitor com.apple.CloudDocs

## Gather iCloud diagnostics archive (saves to Desktop by default)

    brctl diagnose

## Gather diagnostics to a specific destination

    brctl diagnose -d ~/Desktop/icloud-diag

## Show help

    brctl help
