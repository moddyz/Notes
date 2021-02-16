# Linux Systems Programming Notes

First-pass-reading notes of "Linux System Programming".

## Table of Contents

- [Introduction and Essential Concepts](#introduction-and-essential-concepts)

## Introduction and Essential Concepts

- _System calls_ are invocations made from _user-space_ into the _kernel-space_.
- _API_ is the source-code level interface between software.
- _ABI_ is the binary interface (machine code interactions).
- _POSIX_ == Portable Operating System Interface
- In Linux, everything is a file, which can be opened, read, written to, and copsed
- A _file descriptor_ is a handle of an opened file.
- Regular files contain linear array of bytes, also called a _byte stream_.  No structure is enforced on a regular file.
- Operations against a file start at a byte known as the _file position_ or _offset_.
- A file can be opened multiple times.  Each time it is open, it returns a unique file descriptor to the caller.
- Processes can share file descriptors to other(s) to be used.
- Concurrent access to a single file must be coordinated by user-space programs.
- A file is actually referenced by an _inode_ (information node), assigned a unique numerical value.  An inode does not have a file name.
- A _directory_ is a special file which only contains a mapping of names to inode numbers (referring to other files)
- For a given file open request, the kernel will look up the filename and obtain the associated inode number.  The inode number is used to obtain the inode.  Finally, the inode contains metadata which indicates the physical on-disk location of the data.
- 
