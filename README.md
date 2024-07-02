# clip-io

A package agnostic shim for piping stdout into clipboard and printing clipboard to stdout.

```bash
printf '%s\n' 'hello' | clip-in; clip-out
# stdout: hello
```

## Dependencies
clip-io uses the following dependencies according to the environment:
```bash
X11: 
  - xclip | xsel 

Wayland:
  - wl-copy 
  - wl-paste

Termux:
  - termux-clipboard-set
  - termux-clipboard-get
```
### Note:

`termux-clipboard-{get,set}` will hang unless the [Termux:API](https://wiki.termux.com/wiki/Termux:API) addon is installed.

## Examples
```bash
# Write clipboard to a file
clip-out > clipboard.txt

# Pipe a command into clipboard
date | clip-in

# Pipe a heredoc into clipboard removing trailing newlines
clip-in -r <<-'EOF'
	hello for a heredoc
EOF
```

## License
Licensed under Zero-Clause BSD (0BSD). See LICENSE for details.
