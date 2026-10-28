# Idle Spiral Save Editor (Unofficial)

A free, offline HTML editor for selected **Idle Spiral** save values. No installation, server, account or third-party dependencies are required.

> **Independent community project.** Not affiliated with, endorsed by, or supported by the developers of Idle Spiral. Always create a backup of your save before editing it. Tested on the cross-platform JSON save format from game version **3.0.84**; support for other versions is not guaranteed.

## Features

- Current **R**, **P** and **Z** currency balances (big-number notation)
- **Attack-speed** bonus from Daily Spiral, with convenient multipliers
- Battle-earned **EXP** and **Spiral Points**
- Earned **Inspiration** and **Formula Fragments**
- All 100 indexed **Battle Upgrade** level slots, with searching, filtering, and community-sourced names for selected upgrades
- Verifies the incoming `payloadSha256` and recalculates the game's SHA-256 integrity checksum when exporting
- Changes only selected values inside the existing save-data JSON text, leaving other fields untouched rather than rounding unrelated large numbers
- Runs completely locally in a browser. No requests to the internet are made by the editor.

## Quick start

1. Back up your original `.idlespiral-save` file.
2. Download [`index.html`](index.html) and open it in Chrome, Edge or another current browser. You can also use a static GitHub Pages deployment.
3. Select or drag in your `.idlespiral-save` file.
4. Check for **SHA-256 verified** before changing anything.
5. Edit the chosen values, then choose **Download edited save**.
6. Import the downloaded save in Idle Spiral, and verify the results in-game.

No game save files or game DLLs are included in this repository.

## Important distinctions

- **R / P / Z** edit only the **current balances**, not stored historical maximum or lifetime totals. Some achievements or systems may rely on those separate values.
- **Attack speed** edits the `attackSpeedFromDailySpiral` value, **not** final attacks per second. Actual speed may depend on other bonuses and the game version.
- **Spiral points** edit `spiralPointFromBattle`, which is one source of SP, not necessarily the complete displayed balance.
- **EXP**, **Inspiration** and **Formula Fragments** edit saved earned totals. Their **spent** values remain intact.
- **Battle Upgrade** controls map to indices of `battle_upgrade_levels` (Upgrade 1 = array element 0). Current labels are community descriptions, not verified against every game version. The game may enforce level caps, unlocks or progression rules.
- Any edit, even one with a technically valid checksum, might have unwanted in-game effects. Always test on a backup.

## Privacy & security

The application is a single self-contained HTML file. It uses browser file reading and an in-browser SHA-256 implementation. Files stay on the user's computer; the page contains no analytics, requests, CDNs, remote scripts or upload endpoints. The editor normally blocks exporting a file whose original checksum fails until the user explicitly acknowledges the mismatch.

The format and checksum implementation were tested against an exported Idle Spiral v3.0.84 save. The game may change its save schema and checksum format in later updates.

## Credits & attribution

**Idle Spiral** was developed by **Idle System, Inc., Yayu, and Sumito.O**, and is published by Idle System, Inc. Thanks to the developers for the game. [Official Steam page](https://store.steampowered.com/app/1827980/).

**Save editor created and coded by ChatGPT (OpenAI).** This independent community utility was tested in-game by a player. It is *not* an official OpenAI product or an official Idle Spiral utility.

Selected Battle Upgrade descriptions are based on the [community-maintained Idle Spiral Wiki](https://idle-spiral.fandom.com/wiki/Battle_Upgrades), and may not reflect newer game updates.

## Publishing on GitHub Pages

1. Create a new public GitHub repository, for example `idle-spiral-save-editor`.
2. Upload `index.html`, `README.md`, `LICENSE` and `CHANGELOG.md` to the repository's `main` branch.
3. In the repository choose **Settings → Pages → Build and deployment → Deploy from a branch**, and select `main` / `/(root)`.
4. The site should become available at `https://YOUR-USERNAME.github.io/idle-spiral-save-editor/` after GitHub publishes it.

The file also works without GitHub Pages: download and open `index.html` locally.

## Contributing

Bug reports and pull requests are welcome. If an upgrade number or field changes in a new Idle Spiral release, please include the **game version** and the expected field or upgrade label. Do not post personal save files publicly without checking what they contain. Please do not upload proprietary game DLLs to this repository.

## License

MIT License (see [LICENSE](LICENSE)) for the editor's original code only. This license does not apply to Idle Spiral, its assets or its intellectual property.
