# User Guide

## Product Scope

qBiremo Enhanced is a Windows desktop client for managing a qBittorrent WebUI instance. It is built for high-density review, bulk actions, deep torrent details, and operational tooling.

Use it when you want more table control, filtering, edit panels, tracker insight, and session tooling than the standard WebUI provides.

## Install and First Run

1. Install Python 3.13 or use the portable release package when available.
2. Enable the qBittorrent WebUI in qBittorrent.
3. Confirm the WebUI is reachable in a browser.
4. For a source install, run:

```bat
python scripts\windows\setup_env.py
```

5. Start the GUI:

```bat
pyw scripts\windows\run_app_gui.pyw
```

Use `python scripts\windows\run_app.py` when you want a console window for diagnostics.

## Configure qBittorrent

Prepare:

- WebUI host and port
- HTTP or HTTPS scheme
- username and password
- optional profile id when running multiple configurations

Start with a profile that points to a test or low-risk qBittorrent instance if you are validating workflows for the first time.

## Daily Workflow

1. Start the app and confirm the status bar shows the expected qBittorrent instance.
2. Let the initial torrent list finish loading before using bulk actions.
3. Use quick filters or the left filter tree to narrow the visible torrent set.
4. Inspect details, trackers, peers, and content before changing torrents in bulk.
5. Save useful table views after adjusting visible columns and widths.
6. Use edit actions on one torrent first, then apply bulk actions only after filters are correct.
7. Watch the status bar and task indicator when long-running actions are active.

## Common Tasks

### Filter the Torrent List

Use the quick filter bar for text, private-state, and file-path filtering. Use the left filter tree for status, category, tag, size, and tracker dimensions.

### Review Torrent Details

Select one torrent and use the details tabs for general metadata, trackers, peers, content, and editable fields. Multi-selection disables single-torrent edit fields to avoid ambiguous updates.

### Add Torrents

Use the add-torrent dialog for local `.torrent` files, magnet links, and URLs. Confirm save path, category, tags, behavior options, and limits before submitting.

### Manage Tags and Categories

Use the taxonomy tools to create, edit, or delete tags and categories. Confirm category paths before assigning them to a large selection.

### Manage Speed Limits

Use the speed limits dialog to change normal and alternative global speed limits. Confirm whether alt-speed mode is enabled before troubleshooting slow transfers.

### Export Torrent Files

Use export actions for selected torrents when you need offline backup or migration. Review the destination folder and exported filenames after completion.

## Settings and Data

The app uses profile-aware settings and runtime data. Separate profiles isolate connection details, logs, cache state, and instance locks.

When running multiple instances, use explicit profile ids so each window is clearly tied to the intended qBittorrent configuration.

## Safety Notes

- Remove and remove-with-data actions are destructive.
- Bulk actions apply to the current selection, not just the row you last clicked.
- Saved views change table presentation, not torrent state.
- Content priority changes can affect active downloads immediately.
- Clipboard monitor can auto-detect magnet links and hashes; leave it disabled unless that workflow is intentional.

## Troubleshooting Checklist

- If login fails, verify WebUI URL, username, password, and qBittorrent WebUI settings.
- If the torrent list is empty, check active filters before assuming the API returned no torrents.
- If refreshes are slow, inspect remote filters and large torrent counts.
- If a local path does not open, confirm the path exists on this Windows machine and is not remote-only.
- If an instance will not start, check for an existing profile lock or stale process.

## Getting Help

When filing an issue, include:

- app version
- Windows version
- qBittorrent version
- whether you used the portable package or source install
- sanitized WebUI URL shape, without credentials
- profile id, if relevant
- exact action and filters active when the issue occurred
- relevant logs or console output
