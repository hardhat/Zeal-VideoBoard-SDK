Z     -z (defaults to rle)
args Namespace(input='assets/sphere__B8C12S00Z.gif', tileset=PosixPath('assets/sphere.zts'), palette=PosixPath('assets/sphere.ztp'), bpp=8, compress='rle', colors=18, strip=0)
-z        defaults to rle compression
-z        defaults to rle decompression

## Filename Flags

Filename flags allow you to provide gif2zeal arguments in the filename of your asset.

This is useful when you have multiple assets, and want to use different settings for
each one while still taking advantage of the ZDE Makefile to auto-export Aseprite/GIF
files to ZTS/ZTP.

Filename flags are provided by adding a trailing `__` (double underscore) to the end
of your filename, then providing the flags as follows.

```text
Flag  Argument
----  --------
Bn    -b N
Cxx   -c N
Pxx   -c N
Sxx   -s N
Z     -z (defaults to rle)
R     -z rle
L     -z lz
```

Where `n` is a number, and `xx` is a hex number.  So `S80` will strip 128 tiles, and `B4` will be `-b 4` for 16-color mode

### Example of Filename flags

```text
grid__B1S03.gif
sphere__B8C12S00Z.gif
logo__B4R.gif
```

This produces the equivalent of

```python
args Namespace(input='assets/grid__B1S03.gif', tileset=PosixPath('assets/grid.zts'), palette=PosixPath('assets/grid.ztp'), bpp=1, compress=None, colors=256, strip=3)

args Namespace(input='assets/sphere__B8C12S00Z.gif', tileset=PosixPath('assets/sphere.zts'), palette=PosixPath('assets/sphere.ztp'), bpp=8, compress='rle', colors=18, strip=0)

args Namespace(input='assets/logo__B4R.gif', tileset=PosixPath('assets/logo.zts'), palette=PosixPath('assets/logo.ztp'), bpp=4, compress='rle', colors=256, strip=0)
```

CLI behavior matches the same rule:

```text
-z        defaults to rle compression
-z lz     uses lz compression
-z rle    uses rle compression
		  no compression is applied when -z/--compress is omitted
```

## zeal2gif Compression

The reverse conversion tool uses the same flag shape for decompression.

```text
-z        defaults to rle decompression
-z lz     uses lz decompression
-z rle    uses rle decompression
		  no decompression is applied when -z/--compressed is omitted
```

Example:

```shell
./zeal2gif.py -t sprite.zts -p sprite.ztp -z
./zeal2gif.py -t sprite.zts -p sprite.ztp -z rle
./zeal2gif.py -t sprite.zts -p sprite.ztp
```

## Requirements:

Install Pillow

```shell
pip install pillow
```
