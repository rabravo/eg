# gh


# Workflow Runs

list recent workflow runs for a repo (shows status, branch, event, elapsed time)

    gh run list --repo rabravo/ou-csi3450-container --limit 3


drill into the details of a specific run by its ID

    gh run view 29348963554 --repo rabravo/ou-csi3450-container


stream live output of a run until it completes

    gh run watch 29348963554 --repo rabravo/ou-csi3450-container

