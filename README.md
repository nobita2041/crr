# crr - Claude Code Restart

Restart Claude Code while preserving your session. Works like sending a HUP signal.

## Features

- Restarts Claude Code without losing your conversation context
- Preserves command-line options across restarts
- Supports verbose mode for debugging

## Requirements

- macOS
- iTerm2
- [Claude Code](https://claude.ai/code)

## Installation

```bash
curl -fsSL https://raw.githubusercontent.com/nobita2041/crr/main/crr -o ~/.local/bin/crr && chmod +x ~/.local/bin/crr
```

## Usage

From within Claude Code, use the shell escape:

```
!crr
```

Or from your shell after exiting Claude Code with `Ctrl+C`:

```bash
crr
```

### Verbose Mode

For debugging, use the verbose flag:

```bash
crr -v
```

## How It Works

1. Detects the current iTerm2 TTY
2. Finds the Claude process running on that TTY
3. Extracts the session ID from process arguments (or falls back to the most recent session file)
4. Saves options to `/tmp/claude-opts/` for persistence across restarts
5. Terminates Claude and restarts with `--resume` to continue the session

## Limitations

- Currently only supports iTerm2 on macOS
- Requires Claude Code to be running in the current terminal session

## License

MIT
