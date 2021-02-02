# readelf

`readelf` linux utility.

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
