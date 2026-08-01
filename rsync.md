# rsync

sync a local folder to a backup folder (recursive, preserve links/times)

    rsync -rltDv /path/to/folder/* /path/to/backup/


sync to a remote server, excluding specific directories

    rsync -av --exclude={'script','vendor','sample'} src/ user@server:dest/


dry run to preview what would be transferred

    rsync -av --dry-run src/ user@server:dest/


use checksum (-c) to compare files by content instead of size/timestamp

    rsync -avc src/ user@server:dest/

  without -c, rsync skips a file if size and modification time match.
  with -c, it ignores those and instead:

    1. sender reads each source file and computes an MD4 checksum
    2. receiver computes the same checksum over the corresponding destination file
    3. sender and receiver exchange checksums over the rsync protocol
    4. if checksums differ, the file is scheduled for transfer (using rsync's
       block-level delta algorithm); if they match, the file is skipped
    5. after transfer, a second checksum pass verifies the written data matches
       the source (equivalent to --checksum-seed verification)

  useful when clocks differ between systems or files were touched without
  changing content (e.g. after a restore, a build that rewrites unchanged files).
  costs more CPU and I/O since every file must be read on both ends.


