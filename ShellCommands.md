# Shell Commands

## Table of Contents

- [abidiff](#abidiff)
- [abidw](#abidw)
- [find](#find)
- [nm](#nm)
- [readelf](#readelf)

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
