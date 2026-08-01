# claude -- Claude Code CLI

## Start a session

    claude

## Start with a prompt

    claude "explain this repo"

## Change model for a session (flag)

    claude --model claude-opus-4-7
    claude --model claude-sonnet-4-6
    claude --model claude-haiku-4-5-20251001

## Change model inside a running session

    /model claude-opus-4-7

## Key slash commands

    /help          show all commands
    /clear         clear conversation history
    /compact       summarize history to save context
    /cost          show token usage and cost for this session
    /memory        view and edit persistent memory files
    /exit          end the session

## Run a skill

    /ada week05
    /revealjs-pptx

## Run a shell command without leaving Claude

    ! git status
    ! ls -la

## Toggle fast mode (Opus, faster output)

    /fast
