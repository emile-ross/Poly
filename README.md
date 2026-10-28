# Poly

A single-file terminal console for CTF / cybersecurity-competition teams. Poly gives a small team one shared place for a reference board, role assignments, a per-lane tool checklist, a target board, and a flag tracker. Pure Python standard library, no dependencies, runs on Linux/macOS/WSL.

```
python3 poly.py
```

## Features

- **Skull banner + countdown** on launch, with a configurable event name, team name, and date.
- **Common CTF categories** — a quick reference of what tends to show up (web, pwn, crypto, forensics, networking, OSINT).
- **Role board** — who owns which lane, who backs up whom.
- **Tool checklist** — per-lane install lists so nobody fights their toolchain on the day.
- **Etiquette / notes** — generic good practice; swap in your event's real rules.
- **Targets (IP or link)** — paste an IP, `host:port`, or a URL; it detects which it is, parses it, and shows the matching **manual** methodology checklist (web app vs network host). It records and assigns targets. It does not run anything against them.
- **Flag / challenge tracker** — add challenges, assign owners, mark `todo / wip / done / stuck`. Saved to `poly_flags.json`.
- **setup.sh generator** — writes a role-aware installer that detects `apt` vs `pacman` and installs standard, freely-available tooling.

## Configure

Everything team- and event-specific lives at the top of `poly.py`. Edit the `CONFIG` dict:

```python
CONFIG = {
    "event_name": "CTF",
    "team_tag":   "your team",
    "event_date": "",          # "YYYY-MM-DD" for a countdown, or "" to hide it
    "subtitle":   "team prep + coordination console",
}
```

Then edit the lists just below it: `ROLES`, `CATEGORIES`, `CHECKLIST`, `NOTES`, and `LINKS`. The `NOTES` section is deliberately generic — replace it with your competition's actual rules and any AI-use policy before the event.

## Files it writes

- `poly_flags.json` — the flag/challenge tracker state
- `poly_targets.json` — the target board state
- `setup.sh` — generated on demand from menu option 8

These are created next to the script and are listed in `.gitignore`, so your working state isn't committed.

## Notes

Poly is a coordination and reference tool. The target board gives you a checklist to work through by hand; it is not a scanner or an exploit tool. Keep it that way and it stays fine to use in any competition that allows your own notes and tooling.

## License

MIT. See [LICENSE](LICENSE).
