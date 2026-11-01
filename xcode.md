xcode-select --install
    # Triggers the system popup to install Command Line Tools
    # No full Xcode required — installs git, make, clang, etc.

xcode-select -p
    # Prints the active developer tools path
    # /Library/Developer/CommandLineTools   ← CLT-only install
    # /Applications/Xcode.app/Contents/Developer  ← full Xcode

xcode-select --reset
    # Resets the active tools path back to the system default
    # Useful after switching between Xcode versions

sudo xcode-select --switch /Applications/Xcode.app
    # Switches active tools to full Xcode (requires sudo)
    # sudo xcode-select --switch /Library/Developer/CommandLineTools
    # Switches back to CLT if both are installed
