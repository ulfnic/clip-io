# clip-io

Shim for writing/reading a UNIX-like system's clipboard using the appropriate command for the environment.

```bash
printf '%s\n' 'hello' | clip-in
clip-out
# stdout: hello
```
```bash
clip-in --help
```
```bash
clip-in [ARGUEMENT...] [< INPUT]

Writes stdin into the system clipboard using the appropriate command for the environment.

ARGUEMENT
	-r                         Remove all trailing newlines from INPUT
	-C|--clear-after SECONDS   Clear clipboard if contents are the same as INPUT after SECONDS
	-h|--help                  Print help doc

DEPENDENCIES
	Environments
		X11       xclip || xsel
		Wayland   wl-copy
		Termux    termux-clipboard-set

	Note: termux-clipboard-set will hang unless the Termux:API addon is installed.

	ARGUEMENTs
		-r                 tr
		-C|--clear-after   clip-in, clip-out, md5sum, sleep

EXAMPLES
	# Pipe current date into clipboard
	date | clip-in

	# Remove all trailing newlines from INPUT
	printf '%s\n\n\n' 'no newline(s) after this' | clip-in -r

	# Clear clipboard if it contains "my secret" after 8 seconds
	printf '%s' 'my secret' | clip-in --clear-after 8
```
```bash
clip-out --help
```
```bash
clip-out [ARGUEMENT...]

Writes system clipboard to stdout using the appropriate command for the environment.

ARGUEMENT
	-r          Remove all trailing newlines from output
	-h|--help   Print help doc

DEPENDENCIES
	Environments
		X11       xclip || xsel
		Wayland   wl-paste
		Termux    termux-clipboard-get

	Note: termux-clipboard-get will hang unless the Termux:API addon is installed.

	ARGUEMENTs
		-r   tr

EXAMPLES
	# Write clipboard to a file
	clip-out > clipboard.txt
```
