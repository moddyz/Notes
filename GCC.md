# GCC

## Table of Contents

- [Compiling](#compiling)

## Compiling 

Preprocess a source file:
```bash
g++ -E <SOURCEFILE>
```

Preprocess and compile a source file:
```bash
g++ -S <SOURCEFILE>
```
 
Preprocess, compile, and assemble (convert assembly to target machine code) a source file into an object file (without linking):
```bash
g++ -c <SOURCEFILE>
```

Enable all warnings: 
```bash
-Wall
```
 
Enable position independent code (for linking objects into shared libraries - addresses in the generated code will be relative to a global offset table, and resolved at load-time of executable.):
```bash
-fPIC
```

Common C++ standard options:
```bash
--std=c++98 
--std=c++11
--std=c++14
--std=c++17
--std=c++20
```

Debugging options:
```bash
-g[0-3] # Produces debug information
-ggdb[0-3] # Produces debug information for gdb.
```

Optimization options: 
```bash
-O0 # Default, no optimization.
-O1
-O2
-O3 # Full optimization.
-Og # Optimize for debug experience.  Includes some passes even -O0 may skip.
```
