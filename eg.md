# eg

## NAME

eg – show practical usage examples for command-line programs

## SYNOPSIS

    eg [OPTIONS] [program]

## DESCRIPTION

eg provides concise, annotated examples of common command usage.
It ships with a curated set of example files and supports a user-defined
custom directory (default: ~/.eg/) where you can add or override examples
in Markdown format.

Configuration is read from ~/.egrc (INI format). The only option currently
in use is custom-dir, which points to the directory holding user-defined
example files.

## OPTIONS

    eg program
    # Display examples for the named program.

    eg -l
    # List all programs that have eg entries. A leading * means both a
    # default and custom file exist; + means only a custom file exists.

    eg -e program
    # Open the custom example file for program in $VISUAL or $EDITOR.
    # Creates the file if it does not yet exist.

    eg --color program
    eg --no-color program
    # Force color output on or off.

    eg -s program
    # Reduce the number of blank lines in the output (squeeze).

    eg -p "less -R" program
    # Override the pager used to display output.

    eg -c ~/notes/eg-custom program
    # Override the custom examples directory for this invocation.

    eg --examples-dir /path/to/dir program
    # Override the built-in examples directory for this invocation.

    eg -f ~/.egrc program
    # Use a specific config file instead of ~/.egrc.

    eg -v
    # Print version information and exit.

## EXAMPLES

    eg curl
    # Show examples for curl.

    eg --color -s cut
    # Show examples for cut with color and no extra blank lines.

    eg -l
    # List every program that has an entry.

    eg -e docker
    # Edit (or create) a custom example file for docker.

    eg -c ~/notes/eg-custom awk
    # Use a one-off custom directory.

## FILES

    ~/.egrc
    # User configuration (INI format). Recognized keys:
    #   custom-dir = /path/to/dir
    #   editor-cmd = vim
    #   pager-cmd  = less -R
    #   color      = true

    ~/.eg/
    # Default custom examples directory. Each file is named <program>.md.

## SEE ALSO

man(1), tldr(1)

## VERSION

1.2.3
