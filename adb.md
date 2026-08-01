# adb

install adb via Homebrew (Android Platform Tools)

    brew install android-platform-tools

    # installs adb, fastboot, and related tools
    # verify with: adb version


list connected devices

    adb devices

    # adb devices    list all attached devices and emulators
    # columns:       serial number (e.g. emulator-5554 or device USB id)
    #                state — device, offline, unauthorized


open a shell on the device

    adb shell

    # drops you into an interactive shell on the connected device
    # exit with Ctrl-D or typing exit


run a single shell command on the device

    adb shell ls /sdcard/


target a specific device when multiple are connected

    adb -s emulator-5554 shell

    # -s <serial>    select device by serial number shown in `adb devices`



# File Transfer

copy a file from your Mac to the device

    adb push ~/Downloads/file.txt /sdcard/Download/

    # adb push <local> <remote>    copy local file to device path


copy a file from the device to your Mac

    adb pull /sdcard/Download/file.txt ~/Downloads/

    # adb pull <remote> <local>    copy device file to local path


copy an entire directory from the device

    adb pull /sdcard/DCIM ~/Downloads/DCIM



# App Management

install an APK

    adb install app.apk

    # adb install    sideload an APK onto the connected device


install, replacing an existing version

    adb install -r app.apk

    # -r    reinstall, keeping the app's data


uninstall an app by package name

    adb uninstall com.example.myapp


list all installed packages

    adb shell pm list packages

    # pm list packages    package manager — lists every installed package name


list only third-party (user-installed) packages

    adb shell pm list packages -3



# Logcat

stream device logs

    adb logcat

    # press Ctrl-C to stop


filter logs by tag

    adb logcat -s MyAppTag

    # -s <tag>    show only log lines with this tag


filter by minimum priority (V D I W E F)

    adb logcat *:W

    # *:W    show Warnings, Errors, and Fatals from all tags


clear the log buffer then stream

    adb logcat -c && adb logcat



# Screen Capture

take a screenshot and pull it to the current directory

    adb shell screencap /sdcard/screen.png && adb pull /sdcard/screen.png .


record the screen for up to 3 minutes (stops on Ctrl-C)

    adb shell screenrecord /sdcard/demo.mp4

    # pulls automatically after stopping:
    adb pull /sdcard/demo.mp4 .



# Network and Port Forwarding

forward a device port to the host (e.g. for a debug server)

    adb forward tcp:8080 tcp:8080

    # adb forward tcp:<host-port> tcp:<device-port>


list active forwards

    adb forward --list


remove all forwards

    adb forward --remove-all


connect to a device over Wi-Fi (Android 11+, wireless debugging)

    adb pair <ip>:<pair-port>     # enter the pairing code shown on device
    adb connect <ip>:<port>       # connect after pairing



# Backup and Restore

back up the entire device (apps + shared storage) to a file

    adb backup -all -apk -shared -f backup.ab

    # -all      include all installed apps
    # -apk      include the APK files themselves (not just app data)
    # -shared   include shared storage (/sdcard)
    # -f        output file path on the host


back up a single app by package name

    adb backup -apk -f myapp.ab com.example.myapp


back up only app data, no APKs, no shared storage

    adb backup -all -noapk -noshared -f appdata.ab

    # -noapk      skip APK files
    # -noshared   skip shared storage


restore from a backup file

    adb restore backup.ab

    # confirm the restore prompt on the device screen


inspect the contents of a backup file (converts .ab to a tar archive)

    dd if=backup.ab bs=24 skip=1 | python3 -c "import zlib,sys; sys.stdout.buffer.write(zlib.decompress(sys.stdin.buffer.read()))" | tar -tv

    # backup files are: 24-byte header + zlib-compressed tar
    # -tv    list contents without extracting



# Device Info

show device model, Android version, and other properties

    adb shell getprop | grep -E 'ro.product.model|ro.build.version.release'


reboot the device

    adb reboot


reboot into bootloader (fastboot mode)

    adb reboot bootloader


reboot into recovery

    adb reboot recovery


