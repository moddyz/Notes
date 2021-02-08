# GDB

## Table of Contents

- [Configuration](#configuration)
- [Invocation](#invocation)
- [Logging](#logging)
- [Environment](#environment)
- [Inferiors](#inferiors)
- [Breakpoints](#breakpoints)
- [Watchpoints](#watchpoints)
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

## Invocation

```bash
# Start gdb with a program.
gdb <PROGRAM>

# Start gdb with a program and additional program arguments.
gdb --args <PROGRAM> <PROGRAM_ARGS>
```

## Logging

```bash
# Log to a specified file.
set logging file <FILE>
```

## Environment

```bash
# Show all environment variables.
show environment

# Set an environment variable.
set environment <VARNAME> <VALUE>

# Unset an environment variable.
unset environment <VARNAME>
```

## Inferiors

```bash
```

## Breakpoints

```bash
# Insert a breakpoint at location.
break <LOCATION>

# Insert a breakpoint which only stops once at location.
tbreak <LOCATION>

# Insert a breakpoint onto functions matching the regular expresion.
rbreak <REGEX>

# Show all breakpoints.
info breakpoints

# Delete specified breakpoint
del breakpoints <BREAKPOINT_NUM>

# Delete all breakpoints
del breakpoints

```

## Watchpoints

A "data" breakpoint.

```bash


```

## TUI Mode

```bash
# Enter TUI mode.
Ctrl-x a

# Previous command.
Ctrl-p

# Next command.
Ctrl-n

# Change window focus.
Ctrl-x o
```
