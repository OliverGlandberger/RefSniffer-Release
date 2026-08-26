# RefSniffer

A desktop companion pane for LLM coding CLIs. It watches the transcript files your CLI writes and gives you two things:

- **The whole fleet at a glance** -- which session is working, which is waiting on you, which has replies you have not read.
- **Code references you can actually inspect** -- every `src/File.ts:42` in a reply becomes a card showing the real lines, resolved from what the AI actually read rather than guessed at.

It is a read-only viewer. It never talks to an LLM and never edits your files.

## Download

Latest build: **[Releases](../../releases/latest)**

| OS | File | Needs |
|---|---|---|
| Windows | `RefSniffer_<version>_x64-setup.exe` | Windows 10 1803+. Installs the WebView2 runtime if it is missing. |
| macOS | `RefSniffer_<version>_universal.dmg` | Apple Silicon or Intel. **Drag it to Applications** -- see below. |
| Linux | `RefSniffer_<version>_amd64.AppImage` | glibc 2.35+ (Ubuntu 22.04+, Debian 12+, Fedora 36+). `chmod +x`, then run. |

### Expect a warning the first time

The builds are **not code-signed yet**. Windows will say *"Windows protected your PC"*: click **More info**, then **Run anyway**. macOS will ask you to allow it under **System Settings > Privacy & Security**. The AppImage needs no signature.

That is deliberate for now. RefSniffer goes directly to people who are told to expect this, rather than being published to strangers, and signing lands before that changes.

**macOS: drag the app to Applications before running it.** Launching it from the mounted disk image makes macOS run it from a temporary location, which breaks both updates and the Claude Code integration.

## What it does on the network

Nothing, unless you turn on the update check. That check ships **off** and asks you once. While it is off, RefSniffer makes no network connections at all, and that is meant to be verifiable with a firewall rather than taken on trust. Turned on, it downloads a small file naming the newest version, and installs nothing until you ask it to.

No telemetry, ever.

One thing worth stating rather than implying: RefSniffer can optionally *host* your CLI in an embedded terminal. In that mode the CLI reaches its own service exactly as it does in your own terminal. RefSniffer is the parent of a program that opens sockets, not the thing opening them.

## Something wrong?

Open an [issue](../../issues). Logs live in `~/.refsniffer/logs/` and record paths, counts and timings, never the content of your conversations.

## License

Free of charge under a short freeware licence. The source is private. Every download carries its licence and the open-source notices for the components it bundles.
