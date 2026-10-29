# herdr

# Typical usage: start Claude Code in a sibling pane

launch herdr from Ghostty (vanilla config)

    open -n -a Ghostty --args --config-file=$HOME/.config/ghostty/config-herdr

verify you are inside a Herdr-managed pane

    test "${HERDR_ENV:-}" = 1 && echo "Inside Herdr"

split a new pane to the right (stay focused here)

    herdr pane split --current --direction right --cwd "$PWD" --no-focus

start Claude in the new pane (use pane_id from split result)

    herdr agent start coder --kind claude --pane w1:p2

send a prompt and wait for it to finish

    herdr agent prompt coder "Review the current diff and list actionable findings." --wait

read the output

    herdr agent read coder --source recent-unwrapped --lines 100

send a key to unblock an agent waiting for approval

    herdr agent send-keys coder enter

install the Claude Code integration (once, outside Herdr)

    herdr integration install claude


# Keyboard Shortcuts (prefix: ctrl+s)

split pane horizontally (below)

    ctrl+s  -

split pane vertically (right)

    ctrl+s  %

focus pane left / down / up / right

    ctrl+s  h / j / k / l

cycle to next / previous pane

    ctrl+s  tab / shift+tab

new tab

    ctrl+s  c

previous / next tab

    ctrl+s  p / n

switch to tab by number

    ctrl+s  1..9

close tab

    ctrl+s  shift+x

close pane

    ctrl+s  x

reload config

    ctrl+s  r


# Basic commands

launch or attach to the persistent session

    herdr


launch a named session

    herdr --session myproject


attach through SSH to a remote herdr server

    herdr --remote user@host


show local client and server status

    herdr status


update to the latest version

    herdr update


generate zsh completions

    herdr completion zsh


print the default configuration

    herdr --default-config



# Sessions

list all sessions

    herdr session list


attach to a named session

    herdr session attach myproject


stop a session

    herdr session stop myproject


delete a stopped session

    herdr session delete myproject



# Workspaces

list workspaces

    herdr workspace list


create a workspace

    herdr workspace create


focus a workspace by id

    herdr workspace focus <id>


rename a workspace

    herdr workspace rename <id> newname


close a workspace

    herdr workspace close <id>



# Worktrees

list git worktree workspaces

    herdr worktree list


create and open a new git worktree

    herdr worktree create


open an existing git worktree

    herdr worktree open <path>


remove a worktree checkout

    herdr worktree remove <path>



# Tabs

list tabs

    herdr tab list


create a tab

    herdr tab create


focus a tab by id

    herdr tab focus <id>


rename a tab

    herdr tab rename <id> newname


close a tab

    herdr tab close <id>



# Panes

list panes

    herdr pane list


show the current pane

    herdr pane current


split the current pane

    herdr pane split


focus a neighboring pane (direction: left, right, up, down)

    herdr pane focus --direction right


zoom/unzoom the current pane

    herdr pane zoom


read terminal output from a pane

    herdr pane read <id>


run a command in a pane

    herdr pane run <id> -- ls -la


send text to a pane

    herdr pane send-text <id> "echo hello"


close a pane

    herdr pane close <id>



# Agents

list running agents

    herdr agent list


show an agent

    herdr agent get <id>


focus an agent

    herdr agent focus <id>


submit a prompt to an agent

    herdr agent prompt <id> "fix the failing test"


wait for an agent to reach a state (idle, busy, stopped)

    herdr agent wait <id> --state idle


read agent terminal output

    herdr agent read <id>


start a supported interactive agent in an existing pane

    herdr agent start <pane-id>



# Server

stop the running server

    herdr server stop


reload config.toml without restarting

    herdr server reload-config


print the live session snapshot

    herdr api snapshot



# Integrations

show integration status

    herdr integration status


install an integration

    herdr integration install <name>


uninstall an integration

    herdr integration uninstall <name>



# Update Channel

show the current update channel

    herdr channel show


switch to the preview channel

    herdr channel set preview


switch back to stable

    herdr channel set stable
