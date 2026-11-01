start the MongoDB server (macOS Homebrew arm64)

    brew services start mongodb/brew/mongodb-community@8.3


stop the MongoDB server (macOS Homebrew arm64)

    brew services stop mongodb/brew/mongodb-community@8.3


restart the MongoDB server (macOS Homebrew arm64)

    brew services restart mongodb/brew/mongodb-community@8.3


list all MongoDB services and their status

    brew services list | grep mongo


start MongoDB (Linux systemd)

    sudo systemctl start mongod


stop MongoDB (Linux systemd)

    sudo systemctl stop mongod


check what process is using port 27017

    lsof -i :27017


kill a mongod process by PID

    kill <pid>
