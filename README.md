# tldr-fmt
Format [tldr](https://tldr.sh/) pages or similar for terminal display

Implemented as a strict POSIX shell script with some formatting and style
options, including word-wrapping (off by default).

### Usage
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

Note: `tldr-fmt` only does formatting - it does not fetch or cache pages, etc.


# ttldr
Tiny tldr client which only finds/fetches the page, and uses `tldr-fmt` for
display, also implemented as a strict POSIX `sh` script.

The tldr pages archive is download and kept as a zip file (never extracted),
and `ttldr` updates it when it's older than 30 days.

`tldr-fmt` is expected at `$PATH`, but if it's not then `ttldr` tries to find
it at the same dir as `ttldr` itself  (possibly following a symlink), so it's
usually enough to symlink only `ttldr` e.g.:
```sh
cd tldr-fmt && ln -s "$PWD"/ttldr ~/.local/bin/  # or some other dir at $PATH
```

### Usage
```
Usage: ttldr CMD | PLAT/CMD | LANG/[PLAT]/CMD  [tldr-fmt options]...
Tiny tldr client, uses tldr-fmt for display.

Usage examples: ttldr curl, ttldr linux/curl, ttldr it//curl, etc.

Display the tldr page for CMD [on platform PLAT], in [LANG or] English.
Languages: es, it, ko, pt_BR, zh, or any other which tldr supports.

Default values and environment variables for overrides are documented
at the `# defaults' section of this script: `which ttldr`
Requires: curl, unzip, tldr-fmt. Home: https://github.com/avih/tldr-fmt
```
