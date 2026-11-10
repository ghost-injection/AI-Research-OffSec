# AI RESEARCH & OFFSEC

Operator tooling and note-grade research from the Ghost Injection persona. Small,
readable, Windows-first utilities that answer one question well instead of pretending
to be a platform.

Everything here runs with the Python standard library. No pip install, no service, no
telemetry.

## Contents

| Project | Platform | What it answers |
|---|---|---|
| [`pid-sniper/`](pid-sniper/) | Windows | Which process owns this window, where is its binary, and what just popped up on screen? |

### pid-sniper

Arm it, click a window, get the PID, process name, window class, and full executable
path. The desktop build adds parent PID and a watcher for *transient consoles* - the
cmd window a stager, installer, or scheduled task opens and closes in under a second.

`popup_watch.py` is the radar by itself: it polls for new top-level windows (dialogs,
toasts, browser popups, message boxes) and prints one JSON object per popup, which is
how a credential prompt announces itself.

```bat
pythonw pid_sniper.pyw              :: click-to-identify, no console window
pythonw pid_sniper_desktop.pyw      :: adds parent PID and transient-console watch
python popup_watch.py --seconds 60  :: headless radar, one JSON object per new window
python popup_watch.py --seconds 60 --all   :: include windows that already existed
```

`popup_watch.py` is importable (`from popup_watch import PopupRadar`) as well as
CLI-runnable, so the radar can feed your own alerting instead of a GUI. Captures stay
in memory until you copy them out.

## What belongs in this repo

Utilities that inspect a live Windows box and can be audited in a single sitting.
Anything that needs a build system, a database, or a config file belongs in its own
repository.

## What does not

- Credential theft, persistence, or anything that runs on a machine you do not own.
- Samples, dumps, or customer data.
- Half-finished ideas with a README longer than the code.

## Requirements

Windows 10/11, Python 3.10+ with Tk (bundled in the python.org installer). The GUI
modules raise on non-Windows platforms by design rather than half-working.

## License

MIT.
