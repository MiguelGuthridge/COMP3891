A [[syscall]] which opens a [[file]], potentially creating it if it doesn't exist.

Returns a [[file descriptor]]. The [[operating system|OS]] must map between a [[process]]'s file descriptors and the corresponding [[vnode|vnodes]].

```c
int open(const char *filename, int flags);
int open(const char *filename, int flags, mode_t mode);
```

## Flags
Options while interacting with the file

## Mode
Options to associate with the file (`drwxrwxrwx`)
