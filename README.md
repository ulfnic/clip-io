# clip-io

A package agnostic shim for piping stdout into clipboard and printing clipboard to stdout.

## Usage Examples
```bash
# Write clipboard to a file
clip-out > clipboard.txt

# Place date inside clipboard
date | clip-in

# Feed a herestring into clipboard removing trailing newlines
clip-in -r <<< '
some text
'
```

## Installation
```bash
cd /usr/local/bin
sudo wget https://raw.githubusercontent.com/ulfnic/clip-io/main/clip-in
sudo wget https://raw.githubusercontent.com/ulfnic/clip-io/main/clip-out
sudo chmod +x clip-in clip-out
```

## Dependencies

```bash
X11: 
  - xclip | xsel 

Wayland: 
  - wl-copy 
  - wl-paste 
```

## License
Licensed under Zero-Clause BSD (0BSD). See LICENSE for details.
