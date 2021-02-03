# Shell Commands

## Table of Contents

- [find](#find)
- [readelf](#readelf)

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

