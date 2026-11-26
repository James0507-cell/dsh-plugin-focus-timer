# Focus Kit - a data-only DSH Mobile plugin

Focus Kit is version 2.0.0 of the **sample.focus-timer** declarative plugin pack for DSH Mobile,
rebuilt on the app's component ecosystem. A pack is one JSON file of data; the app has a compiled
interpreter for it, so installing this repository changes what the app shows but never executes code
from it.

This is the sample used for the **install from a Git repository** flow, now with a working one-block
ritual instead of a demo page.

## What it adds

- A **docked Focus page** (`focus`, dock icon pulse, order 210) with a 25-minute local timer, the three-step
  start ritual, a stall callout, prompt chips, a quote and a block spec.
- A **Focus details page** (`details`) with an accordion on how the timer works, why a pack cannot run a
  background timer, how to update it and how to fork it, plus the list of what stays on the device.
- A **FOCUS TIMER** card on the Now screen: one banner and one copy action, deliberately light.
- A **FOCUS KIT** section in Settings with the plugin id, version, repository and update path.
- A **FOCUS** composer chip that inserts a 25-minute block instruction.
- The **Focus Amber** palette: an amber accent (`#D97706` light, `#FBBF24` dark) derived from the bundled
  `concept-01` ("Refined Ember") palette.

## Component showcase

| Surface | Components | Local interaction |
|---|---|---|
| Focus page (docked) | heading, paragraph, timer, checklist, callout, chips, quote, keyValue | timer countdown, checklist ticks |
| Focus details page | heading, accordion, bullets, divider | accordion expand/collapse |
| FOCUS TIMER home card | banner | none (actions only) |
| FOCUS KIT settings section | keyValue | none (actions only) |

The two interactive families on the Focus page keep their state in the renderer, never in the pack
file: the countdown resets when you leave the page and the checklist is a local tally.

## Actions

| Where | Label | Type | Effect |
|---|---|---|---|
| Focus page | OPEN WORK | open-screen | switches the dock to Work |
| Focus page | COPY FOCUS PROMPT | copy | copies a 25-minute focus prompt, shows a toast |
| Focus page | DETAILS | open-page | opens the details page |
| Focus page banner / home card | OPEN FOCUS | open-page | opens the Focus page |
| Focus details page | BACK TO FOCUS / OPEN SETTINGS | open-page / open-screen | back, or the Settings screen |
| Home card / settings section | COPY PROMPT, OPEN DETAILS | copy / open-page | prompt, or the details page |

The copy action is new in the pack vocabulary: it writes its value to the clipboard and confirms with
a toast. The prompt is real text, not a placeholder - paste it into a session and replace the
angle-bracket line.

## Install from Git

1. Open the app and go to **Settings -> Plugins**.
2. Tap **INSTALL PLUGIN**.
3. Choose **FROM GIT REPOSITORY**.
4. Paste the repository URL:

   https://github.com/James0507-cell/dsh-plugin-focus-timer

5. Check the preview (id `sample.focus-timer`, name "Focus Kit", version `2.0.0`) and confirm.

The app downloads the repository archive, finds `dsh-plugin.json` at the repository root, validates it
against the pack schema, and only then installs it as `files/plugins/sample.focus-timer.json`.

Because this pack is installed from Git, the plugin manager's update check can find later releases.
Reinstall the file or the repository URL to update by hand.

## Or install from the raw file

Download <https://raw.githubusercontent.com/James0507-cell/dsh-plugin-focus-timer/main/dsh-plugin.json>,
then use **Settings -> Plugins -> INSTALL PLUGIN -> FROM FILE**.

## It is data only

- No code, no scripts, no WebView, no network calls, no background timer, no storage. The timer is a
  widget in this page and the prompt lives on the clipboard.
- Actions come from the closed vocabulary the app executes: `open-screen`, `open-page`, `toast`,
  `copy`, `set-plugin-enabled` and `set-config`.
- Strict JSON: unknown fields are refused rather than ignored, so a typo is a visible install error.
- Limits: at most 64 KiB, 12 pages, 8 blocks per slot, 24 rows and 6 actions per body/card, 18
  components per body/card, 8 composer chips, 8 themes.

## Files

- `dsh-plugin.json` - the whole plugin (pack schema `apiVersion` 1).
- `README.md` - this file.
- `LICENSE` - MIT.

The plugin id `sample.focus-timer` is reserved by this repository; fork the repository and use a
different id for your own pack.
