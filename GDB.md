# GDB

## Table of Contents

- [Configuration](#configuration)
- [TUI Mode](#tui-mode)

## Configuration

```bash
# Remember command history across gdb sessions.
set history save on

# Enable pretty printers.
set print pretty on

# Don't paginate (ie. when printing backtraces).
set pagination off

# Live dangerously.
set confirm off
```

## TUI Mode

```bash
# Enter TUI mode.
Ctrl+X A

# Previous command.
Ctrl-P

# Next command.
Ctrl-N
```
