# watchman

install watchman via Homebrew (permanent fix for Metro EMFILE errors)

    brew install watchman

    # Metro (Expo/React Native bundler) auto-detects watchman and uses it
    # instead of Node's fs.watch, which hits macOS open-file-descriptor limits
    # with large node_modules trees (EMFILE: too many open files)


start Expo after installing watchman

    npx expo start

    # no extra flags needed — Metro picks up watchman automatically


raise the file-descriptor limit for the current session (temporary workaround)

    ulimit -n 65536 && npx expo start

    # use this only when watchman is not available
    # the limit resets when the terminal session closes


check that watchman is running

    watchman version

    # prints the installed version
    # watchman starts its daemon on first use; no manual daemon start needed
