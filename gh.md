# gh


# Authentication

authenticate interactively, choosing HTTPS as the protocol and token as the auth method

    gh auth login

    # gh auth login            — start the interactive login flow
    # prompted: GitHub.com     — choose GitHub.com (vs. GitHub Enterprise)
    # prompted: HTTPS          — choose HTTPS as the git protocol (vs. SSH)
    # prompted: token          — choose "Paste an authentication token" (vs. browser login)
    # prompted: paste token    — enter a Personal Access Token (classic or fine-grained)

verify the current authentication status

    gh auth status

    # gh auth status           — show which account is logged in and what scopes the token has


# Workflow Runs

list recent workflow runs for a repo (shows status, branch, event, elapsed time)

    gh run list --repo rabravo/ou-csi3450-container --limit 3

    # gh run list            — list workflow runs for a repo
    # --repo OWNER/REPO      — target repository (defaults to current git remote if omitted)
    # --limit N              — show only the N most recent runs


drill into the details of a specific run by its ID

    gh run view 29348963554 --repo rabravo/ou-csi3450-container

    # gh run view            — show details of a single workflow run
    # RUN_ID                 — numeric ID from `gh run list`
    # --repo OWNER/REPO      — target repository


stream live output of a run until it completes

    gh run watch 29348963554 --repo rabravo/ou-csi3450-container

    # gh run watch           — stream logs of a run in real time, blocking until it finishes
    # RUN_ID                 — numeric ID from `gh run list`
    # --repo OWNER/REPO      — target repository


# File Contents

fetch a file from a private repo and decode it locally (pipe into base64 -d to get plain text)

    gh api repos/rabravo/shela/contents/SheLa_comparison_explorer.html --jq '.content' | base64 -d > file.html

    # gh api                  — call the GitHub REST API
    # repos/OWNER/REPO/       — path to the repository
    # contents/PATH           — GitHub endpoint that returns a file's metadata + base64-encoded content
    # --jq '.content'         — extract only the content field from the JSON response
    # | base64 -d             — decode the base64 string back to plain text
    # > file.html             — save the result to a local file

compare a local file against its GitHub version (no output = identical)

    gh api repos/rabravo/shela/contents/SheLa_comparison_explorer.html --jq '.content' | base64 -d > /tmp/github_copy.html
    diff local_file.html /tmp/github_copy.html

    # diff FILE1 FILE2        — compare two files line by line; no output means they are identical

