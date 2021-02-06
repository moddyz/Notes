# Shell Commands

## Table of Contents

- [abidiff](#abidiff)
- [abidw](#abidw)
- [dpkg](#dpkg)
- [find](#find)
- [nm](#nm)
- [readelf](#readelf)
- [uname](#uname)
- [watch](#watch)

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

## find

```bash
# Find and execute a command per-result (substituted into {}).
find <FIND_ARGS> -exec <COMMAND> {} \;

# Find and execute a single command for all results (substituted into {})
find <FIND_ARGS> -exec <COMMAND> {} +
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
