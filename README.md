# eg — personal cheatsheets

Custom example files for [eg](https://github.com/srsudar/eg), a tool that shows practical, annotated usage examples for command-line programs.

## Usage

```bash
eg <program>       # show examples for a program
eg -l              # list all programs with entries
eg -e <program>    # open (or create) a custom example file in $EDITOR
```

## Setup

Install `eg` and point it at this directory:

```bash
pip install eg
```

Add to `~/.egrc`:

```ini
[eg]
custom-dir = ~/.eg
```

## Cheatsheets

| | | | | |
|---|---|---|---|---|
| adb | awk | basename | bc | bg |
| blkid | brctl | bzip2 | chmod | claude |
| conda | crontab | curl | cut | df |
| diff | dig | dirname | dmesg | docker |
| dot | du | eg | env | fg |
| file | find | fzf | getfacl | gh |
| git | gosu | head | ip | jobs |
| jq | kill | ldd | lftp | ln |
| lsblk | lsof | mamba | mc | mmv |
| mount | mtr | nc | netstat | nmap |
| open | openssh | pdftk | ping | printf |
| ps | read | readlink | rename | rsync |
| screen | script | sed | set | sort |
| split | srun | ssh | ssh-keygen | strace |
| su | sudo | tail | tar | tee |
| tmux | tr | trap | tree | ulimit |
| umount | uniq | usermod | vim | wait |
| wc | wget | xargs | xset | xxd |
| yazi | zoxide | | | |

## File format

Each file is named `<program>.md`. Short description, then a 4-space-indented code block, with `#` comments explaining non-obvious flags:

```
copy a file to a remote host

    scp file.txt user@host:/remote/path/

    # scp    secure copy over SSH
    # -r     copy a directory recursively
```

Sections group related commands under a `# Section Name` heading.
