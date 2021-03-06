# Organised collection of common file extensions

This project maintains reusable collections of common file extensions
categorised per typology. It can be used by any program to quickly
distinguish between file types. It acts faster than mime/type or
libmagic recognition, but is of course less precise.

## Organisation

Each category is a file named after a generic typology stored in `data/`:
- archiv :: archives and disc images
- audio :: playable audio
- book :: electronic books
- code :: code in machine languages
- exec :: executable binaries
- font :: typography fonts
- image :: static images
- sheet :: spreadsheets
- slide :: presentations and slides
- text :: text in human languages
- video :: moving images
- web :: web developers bread and butter

Inside each category file there is a file extension string on each new
line. This collection is not complete... and knowing how standards go:
it will never be. [We welcome your
contribution](https://github.com/dyne/file-extension-list/pulls).

Some extensions (for instance `html`, see #10 and #11) may belong to
more than one category: `code` or `web`. In these cases any extra
occurrance of the extension will be followed by space and a `%` on the
same line to mark it as duplicate of another categorisation that took
priority.

To establish the category of a single file one can simply ignore all
duplicate extensions containing `%` on the same line. Duplicates may
be useful to establish the category of a directory containing multiple
files [by means of fuzzy
logic](https://github.com/dyne/file-extension-list/pull/10#issuecomment-529363535).

## Quick start

Launch this script `./render/list`

It will print on your terminal all currently known extensions by category:

```
video: 3g2 3gp aaf asf avchd avi drc flv m2v m4p m4v mkv mng mov mp2 mp4 mpe mpeg mpg mpv mxf nsv ogg ogm ogv qt rm rmvb roq srt svi vob webm wmv yuv
archive: 7z a apk ar bz2 cab cpio deb dmg egg gz iso jar lha mar pak pea rar rpm s7z shar tar tbz2 tgz tlz war whl xpi xz zip zipx
code: am ap awk bash bat c cc class clj cmd command cpp cs css cxx diff el fish go h hpp htm html java js ksh less lua m m4 patch php pl po py pyw qml r rb rs s scss sh sql swift tcl tcsh toml vb vcxproj xcodeproj xml yml zsh
document: bib bst cfg conf csv doc docx ebook emlx eot fig ics inc ini json log md msg odp ods odt org otf pages pdf ppt pptx rst rtf tex ttf txt vcf woff woff2 wpd wps xls xlsx
image: 3dm 3ds ai bmp dds dwg dxf eps gif gpx jpeg jpg kml kmz max png ps psd svg tga thm tif tiff webp xcf yuv
img: qcow qcow2 raw vdi vmdk vmem vmsd vmsn vmss vmtm vmx voa vof
audio: aac aiff ape au dts flac gsm it m3u m4a mid mod mp3 mpa pls ra s3m sid wav wma xm
book: azw azw1 azw3 azw4 azw6 cbr cbz epub mobi
exec: bin crx dat dll exe i msi o out p pyc pyo so wasm
```

## Code

You are meant to write your own code to parse file-extension-list.

To facilitate the task rendered lists are provided

- [by extension, JSON format](pub/extensions.json)
- [by category, JSON format](pub/categories.json)

This repository also contain some example code in [render](render).

The shell script [./render/list](render/list) will print a list of categories and extensions associated on each line.

The lua scripts [./render/json-categories](render/json-categories) and [./render/json-extensions](render/json-extensions) will produce key/value maps per-category and per-extension as those distributed in [pub](pub).

The shell script [build-zsh-parser](render/build-zsh-parser) renders a
file `file-extension-parser.zsh` containing a zsh function
`file-extension-parser()`; This function can then be called with a
filename as argument and it will return its category according to the
archived extensions in `data/`; It relies on a switch case
construction and two string modifier operations that are completely
native to zsh.

To contribute please file a pull request on
https://github.com/dyne/file-extension-list/pulls

## Usage

File-extension-list is used by the software application
[harvest](https://github.com/dyne/harvest) for fast categorization of
large amounts of directories containing multiple file types.

You are welcome to let us know if you are using it too.

## License

File-extension-list is maintained by [Jaromil](/jaromil) and [Puria](/puria)

This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any
means.

In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the
software to the public domain. We make this dedication for the benefit
of the public at large and to the detriment of our heirs and
successors. We intend this dedication to be an overt act of
relinquishment in perpetuity of all present and future rights to this
software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to <https://unlicense.org>
