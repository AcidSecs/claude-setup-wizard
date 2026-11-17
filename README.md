# Setup Wizard for Claude (vn-setup-wizard)

A friendly front door for people new to Claude. It asks one plain question at a time, explains the words project, skill, plugin and connector, and then switches the companion modules on or off through one small settings file.

## What it does
- Explains Claude's parts in plain English before asking anything.
- Creates `Documents\ClaudeSetup\settings.json` (only after you say yes).
- Lets you turn each companion module on or off: Ledger Starter, Handoff Helper, Session Archive, Project Hub, Builder Standards, Network Link.
- Runs a health check on request. If something fails it looks up Anthropic's current docs, proposes a fix and asks before changing anything.

## What it needs
Nothing to install. To write the settings file it uses a file tool (for example Desktop Commander on Windows).

## What it sends
Nothing. It reads and writes one local settings file only.

## Part of a set
Companion plugins: claude-ledger-starter, claude-handoff-helper, claude-session-archive, claude-project-hub, claude-builder-standards, claude-network-link.

Created by Soroosh Hedayat

Designed in Collaboration by: VectorNine Systems Inc. & Acid Secs Productions Inc.

## Data handling

It saves your setup choices in one small settings file on your PC. It reads no personal data. Nothing is sent to the authors of this plugin. We run no server and receive no data, so nothing is retained by us. The plugin sends nothing to any outside service. Everything it makes stays on your own PC or in your own Google Drive and Claude account, and you can delete it any time.
