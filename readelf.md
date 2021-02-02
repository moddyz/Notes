# readelf

`readelf` linux utility.

```bash
# Query SONAME.
readelf -d <LIBRARY>.so | grep SONAME

# Query rpath or runpath
readelf -d <LIB_OR_BIN> | grep RPATH
readelf -d <LIB_OR_BIN> | grep RUNPATH

# Query GCC compilation information of an object file.
readelf -p .GCC.command.line <OBJECT_FILE>
```
