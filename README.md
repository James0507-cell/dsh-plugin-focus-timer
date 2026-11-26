# Focus Timer — a data-only DSH Mobile plugin

Focus Timer is a sample **declarative plugin pack** for DSH Mobile. A pack is one JSON file of data;
the app has a compiled interpreter for it, so installing this repository changes what the app shows
but never executes code from it.

This is the sample used for the **install from a Git repository** flow.

## What it adds

- A docked **Focus** page (dock order 210) with a 25/5 block plan, spec rows, and three actions:
  open the Work screen, show a "Focus block started" toast, and open the details page.
- A second, non-docked **Focus details** page that explains how the sample works.
- A **FOCUS TIMER** card on the Now screen.
- A **FOCUS TIMER** section in Settings that names the plugin id `sample.focus-timer`.
- A **FOCUS** composer chip that inserts:
  `Start a 25-minute focus block; list only the next three actions.`
- The **Focus Amber** palette: an amber accent (`#D97706` light, `#FBBF24` dark) derived from the
  bundled `concept-01` ("Refined Ember") palette.

## Install from Git

1. Open the app and go to **Settings -> Plugins**.
2. Tap **INSTALL PLUGIN**.
3. Choose **FROM GIT REPOSITORY**.
4. Paste the repository URL:

   ```
   https://github.com/James0507-cell/dsh-plugin-focus-timer
   ```

5. Check the preview (id `sample.focus-timer`, name "Focus Timer", version `1.0.0`) and confirm.

The app downloads the repository archive, finds `dsh-plugin.json` at the repository root, validates it
against the pack schema, and only then installs it as `files/plugins/sample.focus-timer.json`. A pack
installed from a repository can later be refreshed with the manager's update check; a pack installed
from a file is updated by importing the new file.

## Or install from the raw file

If you prefer the file flow: download
<https://raw.githubusercontent.com/James0507-cell/dsh-plugin-focus-timer/main/dsh-plugin.json>,
then use **Settings -> Plugins -> INSTALL PLUGIN -> FROM FILE**.

## It is data only

- No code, no scripts, no WebView, no network calls, no background timer, no storage and no Android
  APIs. A timer is not running after the install: the countdown lives in the prompt you send.
- Actions come from a closed vocabulary, executed by the app: `open-screen`, `open-page`, `toast`,
  `set-plugin-enabled`, `set-config`.
- Strict JSON: unknown fields are refused rather than ignored, so a typo is a visible error.
- Limits: at most 64 KiB, 12 pages, 8 home cards, 8 Settings sections, 24 rows and 6 actions per
  card/page, 8 composer chips, 8 themes, 240 characters per row value or note.

## Files

- `dsh-plugin.json` — the whole plugin (schema `apiVersion` 1).
- `README.md` — this file.
- `LICENSE` — MIT.

The plugin id `sample.focus-timer` is reserved by this repository; use a different vendor/name for
your own pack.
