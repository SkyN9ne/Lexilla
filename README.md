# Lexilla #

The Lexilla library contains a set of lexers and folders that provide support for
programming, syntax checking / highlighting and more.

It's usually used in combination with `Scintilla` for source code editors or IDE / ISE environments.

`Lexilla` is made available as both a shared and a static library.

Shared libraries have different extensions on different Operating Systems:
- Linux `lexilla.so`
- Windows `lexilla.dll`
- macOS `liblexilla.dylib`
  
The static library is called `liblexilla.a` when built with GCC or Clang and `liblexilla.lib` when built with MSVC.

Lexilla is developed cross-platform on Windows, Linux, and macOS and it requires a C++17 compiler.

MSVC 2019.4, GCC 9.0, Clang 9.0, and Apple Clang 11.0 are known to work.

MSVC is only available on Windows. GCC and Clang work on Windows and Linux

On macOS, only Apple Clang is available.

Lexilla requires some headers from Scintilla to build and expects a directory named
`scintilla` containing a copy of Scintilla v5+ to be a peer of the Lexilla top level
directory conventionally called `lexilla`

To build using GCC, run `lexilla/src/makefile`:
	`make`

To use Clang, run `lexilla/test/makefile`:
	`make CLANG=1`
On macOS `CLANG` is automatically set so this can be reduced just to:
	`make`

To use MSVC, run `lexilla/test/lexilla.mak`:
	`nmake -f lexilla.mak`

To build a debug version of the library, add `DEBUG=1` to the command:
	`make DEBUG=1`
	
The compiled libraries / binaries are saved into the `lexilla/bin` subdirectory

Lexilla relies on a list of lexers from the `lexilla/lexers` directory. If any changes are
made to the set of lexers then the source and build files can be re-generated with the
`lexilla/scripts/LexillaGen.py` script which requires Python 3 and is tested with 3.7+.

Python behaves inconsistently but one of these will work at least:
	`python3 LexillaGen.py`
    `python LexillaGen.py`
    `py3 LexillaGen.py`
    `py LexillaGen.py`
    `pyw LexillaGen.py`
