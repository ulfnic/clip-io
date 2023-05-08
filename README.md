# clip-io

A package agnostic shim for piping stdout into clipboard and printing clipboard to stdout.

## Installation
```bash
cd /usr/local/bin
sudo wget https://raw.githubusercontent.com/ulfnic/clip-io/main/clip-in
sudo wget https://raw.githubusercontent.com/ulfnic/clip-io/main/clip-out
sudo chmod +x clip-in clip-out
```

## Usage Examples
```bash
# Place date inside clipboard
date | clip-in

# Write clipboard to file
clip-out > clipboard.txt
```

## Dependencies

#### X11:
- `xclip` or `xsel`

#### Wayland:
- `wl-copy`
- `wl-paste`

## License
Licensed under Zero-Clause BSD (0BSD). See LICENSE for details.
