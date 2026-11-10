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

Arm it, click a window, get PID, process name, parent PID, window title, class,
handle, and full executable path. A second mode watches for *new* top-level windows
and logs each one as it appears, which is how a stager, a message box, or a
credential prompt announces itself.

```bat
pythonw pid_sniper.pyw            :: compact capture
pythonw pid_sniper_desktop.pyw    :: full build: parent PID, capture history
python popup_watch.py --seconds 60  :: headless radar, one JSON object per new window
```

`popup_watch.py` is importable and CLI-runnable, so the radar can feed your own
alerting instead of a GUI. Captures stay in memory unless you pass a log path.

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
