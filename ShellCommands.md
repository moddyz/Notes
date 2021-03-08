# Shell Commands

Ubuntu-based.

## Table of Contents

- [bash](#bash)
- [abidiff](#abidiff)
- [abidw](#abidw)
- [dpkg](#dpkg)
- [fc](#fc)
- [find](#find)
- [ls](#ls)
- [nm](#nm)
- [readelf](#readelf)
- [uname](#uname)
- [watch](#watch)

## bash

```bash
# Go to beginning of line.
Ctrl + A

# Go to end of line.
Ctrl + E

# Move cursor one word forward.
Alt + F

# Move cursor one word backward.
Alt + B

# Clear the screen.
Ctrl + l

# Previous command (in history)
Ctrl + p

# Next command (in history)
Ctrl + n
```

## abidiff

```bash
# Compare the ABI of two shared objects.
abidiff <OBJECT_A> <OBJECT_B>
```

## abidw

```bash
# Dump the ABI of a shared object as a XML file.
abidw <OBJECT>
```

## dpkg

```bash
# List installed debian packages.
dpkg -l (<OPTIONAL_FILTER>)

# List all the files associated with a installed debian package.
dpkg -L <PACKAGE>
```

## fc

```bash
# Edit the last command in a text editor and run it after exit.
fc
```

## find

```bash
# Find and execute a command per-result (substituted into {}).
find <FIND_ARGS> -exec <COMMAND> {} \;

# Find and execute a single command for all results (substituted into {})
find <FIND_ARGS> -exec <COMMAND> {} +
```

## ls

```bash
# List by modified time in ascending order.
ls -ltr

# List with human readable file sizes
ls -lh
```

## readelf

```bash
# Query SONAME.
readelf -d <LIBRARY>.so | grep SONAME

# Query rpath or runpath
readelf -d <OBJECT> | grep RPATH
readelf -d <OBJECT> | grep RUNPATH

# Query GCC compilation information of an object file.
readelf -p .GCC.command.line <OBJECT>

# Print symbol table.
readelf -s <OBJECT>
```

## nm

```bash
# Show de-mangled, external symbols.
nm -Cg <OBJECT>
```

## uname

```bash
# Print detailed information about machine name, operating system, and kernel.
uname -a
```

## watch

```bash
# Persistently and periodically print output of command.
watch <COMMAND>
```
