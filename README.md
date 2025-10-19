# clip-io

Shim for writing/reading a UNIX-like system's clipboard using the appropriate command for the environment.

```bash
printf '%s\n' 'hello' | clip-in
clip-out
# stdout: hello
```

## Dependencies
clip-io writes stdin to the following commands according to the environment and their availability.
```bash
# X11
clip-out: xclip -selection clipboard -out || xsel --clipboard --output
 clip-in: xclip -selection clipboard -in  || xsel --clipboard --input

# Wayland
clip-out: wl-paste
 clip-in: wl-copy

# Termux
clip-out: termux-clipboard-get
 clip-in: termux-clipboard-set
```
### Note:

`termux-clipboard-{get,set}` will hang unless the [Termux:API](https://wiki.termux.com/wiki/Termux:API) addon is installed.

## Examples
```bash
# Write clipboard to a file
clip-out > clipboard.txt

# Pipe current date into the clipboard
date | clip-in

# Remove all trailing newlines
printf '%s\n\n\n' 'no newline(s) after this' | clip-in -r

# Pipe a heredoc into clipboard
clip-in <<-'EOF'
	hello from a heredoc
EOF
```
