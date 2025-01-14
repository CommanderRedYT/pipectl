# `pipectl` - a simple named pipe management utility

`pipectl` is a tool to create and manage short-lived named pipes that can be
used to e.g. control a longer-lived program using short commands from elsewhere
in the system without needing a complex IPC mechanism such as UNIX domain
sockets.

## Features

- Create a named pipe using `pipectl -o | long-running-program`
- Send something to that program's stdin using `echo "input line" | pipectl -i`
- Create multiple named pipes simultaneously by naming them with `--name` or `-n`
- Cleans up after itself when the program exits and removes the pipe
- Allows synchronizing writes to the pipe with the `--lock` or `-l` option

![demo screenshot](https://user-images.githubusercontent.com/4077106/147712401-7de95c84-a381-44f8-9b67-74507215f14a.png)

## Usage

```
usage: pipectl [options]

options:
  -h, --help    show this help
  -o, --out     create a pipe and print its contents to stdout
  -i, --in      write stdin to an open pipe
  -n, --name N  use a pipe with a custom name instead of the default
  -f, --force   force create a pipe even if one already exists
  -l, --lock    use flock(2) to synchronize writes to the pipe
```

## Dependencies

- `CMake`

## Building

- Run `cmake -B build`
- Run `make -C build`

## Files

- `src/main.c`: the whole program
