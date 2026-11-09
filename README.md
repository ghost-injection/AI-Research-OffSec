# AI RESEARCH & OFFSEC

Tools and research from the Ghost Injection persona: offensive security utilities,
defensive instrumentation, and AI-assisted analysis, built to be read, audited,
and used without a deployment ceremony.

## Projects

| Project | What it does | Platform |
|---|---|---|
| [`pid-sniper/`](pid-sniper/) | Click any window to get its PID, process and path, with a popup radar that logs new dialogs as they appear | Windows |

## Rules of this folder

1. **One file when possible.** A tool you can copy mid-incident beats a tool you have to deploy.
2. **No dependencies** unless the dependency is the point.
3. **Show the target before you fire.** Destructive actions print their set first and support `--dry-run`.
4. **Real output in the docs.** If a README shows a table or a JSON block, that output came from a real run.
5. **Defensive by default.** Instrumentation stays local; nothing phones home.

## License

MIT per project unless noted otherwise.
