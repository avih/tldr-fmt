# tldr-fmt
Format [tldr](https://tldr.sh/) pages or similar for terminal display

Implemented as a strict POSIX shell script with some formatting and style
options, including word-wrapping (off by default).

Note: it only does formatting - it does not fetch or cache pages, etc.

```
Usage: tldr-fmt [OPTIONS] [FILE]...
Format tldr pages or similar for terminal display.
With no FILE, or when FILE is -, read standard input.

  -w N  Wrap at column N. Negative is from the end.
  -i N  Indent examples by N characters (0..8).
  -b C  Bullet Character when indent is 2 or more.
  -s N  Use styles: 1-yes/force  0-no (plain text).

  -h    Display this help (styles/formats apply).
  -j    Display additional styles/variables help.

Requires: tput or stty if negative -w value is used.
Report issues at https://github.com/avih/tldr-fmt .
```
