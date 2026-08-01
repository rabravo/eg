# ldd

list shared library dependencies of a binary

    ldd /usr/bin/python3


check if a binary has all required libraries

    ldd /path/to/binary | grep "not found"


show detailed information (uses ld.so directly)

    LD_TRACE_LOADED_OBJECTS=1 /usr/bin/python3


list dependencies of a shared library itself

    ldd /usr/lib/libssl.so


find which package provides a missing library (Debian/Ubuntu)

    apt-file search libname.so


find which package provides a missing library (RHEL/Fedora)

    dnf provides libname.so


