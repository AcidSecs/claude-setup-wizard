---
name: setup-wizard
description: Friendly first-time setup for Claude. Use when the user says "set up Claude", "I'm new", "I'm overwhelmed", "what is a project / skill / plugin / connector", or wants to turn the companion modules (ledger starter, handoff helper, session archive, project hub, builder standards, network link) on or off.
---

# Setup Wizard

Goal: calm a new user down. Plain, short English. ONE question at a time. Explain every term the first time you use it. Never change anything before the user says yes.

## Step 0: read the settings file
Settings live in `Documents\ClaudeSetup\settings.json` (Windows) in the user's home folder. Read it with a file tool or Desktop Commander if available.
- Missing: tell the user you will create it, show the content below, ask "OK to create it?", then create it.
- Present: use it. Never overwrite other keys.

Default content:
```json
{
  "schema": 1,
  "naming_style": "PROJECT | TOPIC | V#",
  "modules": {
    "ledger_starter": true,
    "handoff_helper": true,
    "session_archive": false,
    "project_hub": false,
    "builder_standards": true,
    "network_link": false
  },
  "paths": { "archive_folder": "", "ledger_drive_folder_id": "" }
}
```
Every companion skill reads this file first. If its own module is `false`, it does nothing.

## Step 1: the four words (say them simply, then ask which one is confusing)
- **Project**: a folder of chats that share instructions and files. Like a binder for one job.
- **Skill**: a short instruction sheet Claude reads when a job matches. Like a recipe card.
- **Plugin**: a bundle of skills (and sometimes tools) you install in one click.
- **Connector**: a link that lets Claude read or write in another app (Drive, Calendar, email).

## Step 2: ask, one by one
1. "What do you mostly use Claude for?" (offer: writing, coding, research, building apps, mixed)
2. "Do you come from another AI app?" If yes, reassure: nothing to migrate; chats start fresh.
3. Chat naming: "Do you want every chat named `PROJECT | TOPIC | V#`? (V# counts how many times a chat was handed on.)" Save the answer in `naming_style`.
4. Go through the modules ONE at a time. For each say what it does in one sentence, what it needs, and ask on or off:
   - **Ledger Starter**: a Google Drive folder of short rule pages that every chat reads first, so you do not repeat yourself. Needs the Google Drive connector.
   - **Handoff Helper**: when a chat gets long, it writes a short handoff note and opens a fresh chat that continues. Needs Windows, Desktop Commander and Claude in Chrome.
   - **Session Archive** (OFF by default): saves full chats word for word on YOUR PC so a new chat can search them. Say clearly: full chats are stored on disk, nothing is sent anywhere. Ask for the folder (default Documents).
   - **Project Hub**: one status card per project, plus optional notes between projects.
   - **Builder Standards**: rules for building apps (read-aloud button, icons, licence checks, reusable modules, tick-box guides).
   - **Network Link**: a step-by-step guide to link two PCs on your home network with SSH. You do the security steps yourself.
5. Show the final switch list. Ask "OK to save?" Then write the file.

## Step 3: projects and sections
Offer (do not force) a simple project plan: one project per ongoing job.
**Sections in the sidebar** (CONFIRMED in the Claude desktop app on Windows, November 2026): click the three dots next to a chat, choose **Move to section**, then pick a section or **New section**. The three dots on a section itself offer **New section**, **Rename section**, **Move up**, **Collapse others** and **Delete section**. Menu names can differ by app version; if the user does not see them, say so and do not insist.
Suggest three starter sections for a newcomer: **Active**, **Waiting**, **Done**. Example of a power user's way: put the project name (the part before the first `|` in the chat name) as the section name, plus sections such as "Waiting for completion" and "Important sessions". Say clearly it is only an example; each person picks their own.

## Turning a module on or off later
When the user says "turn on session archive" (or off): read the file, show the one change, ask OK, write only that key.

## Health check
When the user says "check my setup": (1) settings file exists and is valid JSON; (2) for each module that is on, confirm what it needs is present (Drive connector, Desktop Commander, Claude in Chrome). Report in plain words. If something fails, search Anthropic's current docs, PROPOSE a fix, and ASK before changing anything.

## Safety
Nothing runs without a clear yes. Nothing is sent anywhere. No personal data is stored in this plugin.

## Guides for steps the user must do
Whenever the user must do a multi-step job themselves (connect an app, install something, request a download), do not write a long reply. Make a tick-box guide: copy `guide/GUIDE_TEMPLATE.html.txt` (in this plugin's folder) to a NEW file named like `My_Guide.html` in the user's Documents folder (the template is stored as .txt on purpose; the copy is a normal web page), change only the GUIDE object near the bottom, and follow the instructions at the top of the template. Make it extremely detailed: about five small steps for each real step, plain English, the reason in brackets, a copy chip for anything to type, and only the steps a human must do. Keep the chat reply short and point to the guide.
