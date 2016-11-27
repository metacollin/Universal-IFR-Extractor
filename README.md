Universal IFR Extractor for macOS
=======================
A simple command line port of donovan6000's Universal IFR Extractor (formerly a windows-only utility).


Utility that can extract the internal forms representation from both EFI and UEFI modules and convert it into a human readable format.

© Original work by 2014 donovan6000
Ported to macOS by metacollin, 2016
<br /><br /><br />
Changelog:

Initial release, synced to v0.6 6/16/2014 of the windows original.

Building
-----------------
There is only one prerequisite, cmake 2.8+.

Building is simple:

``` sh
git clone https://github.com/metacollin/Universal-IFR-Extractor.git
cd Universal-IFR-Extractor
mkdir build && cd build
cmake ..
make
```

This will produce an executable called ifrextractor.  It has no external files or dependencies, so feel free to copy it to `/usr/local/bin` or simply use it outside your path (`./ifrextractor`).

Usage
----------
From the location of the built binary:

``` sh
./ifrextractor input_file # Will check the file type and output UEFI, EFI, or UNKNOWN

./ifrextractor input_file output_file # Will proceed with generating a human readable extraction.
```
