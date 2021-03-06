       =============================================================
       COPYRIGHT NOTE: This source code, and all of its derivations,
       is subject to the "ITU-T General Public License". Please have
       it  read  in    the  distribution  disk,   or  in  the  ITU-T
       Recommendation G.191 on "SOFTWARE TOOLS FOR SPEECH AND  AUDIO
       CODING STANDARDS".
       =============================================================

The UGST P.56 speech voltmeter module, version 3.1 (21/Aug/95), needs the
following files:

# C program code
```
sv-p56.c ........ the speech voltmeter (SV) module itself; needs the
                  prototypes in sv-p56.h
sv-p56.h ........ prototypes and definitions needed by the SV module.
```

# Additional modules needed (see directory ../utl):
```
ugst-utl.c ...... UGST utilities' module: conversion between float and short
                  data formats functions/macros and gain/loss function.
ugst-utl.h ...... prototypes and definitions needed by the UGST utilities'
                  module.
ugstdemo.h ...... prototypes and definitions needed by UGST demo programs.
```

# Demo
```
sv56demo.c ...... Demonstration program for the SV module; needs the files
                  sv-p56.c, ugst-utl.c, ugst-utl.h, and ugstdemo.h in the
                  current directory.
actlevel.c ...... Demo program that only measures the level/min/max/etc for
                  all the files given in the command line. In MSDOS, needs
                  wildargs.obj when using Borland compilers, in order to
                  be able to automatically process commands like
                    actlev *.src
                  This is not a concern in Unix because wildcard expansion
                  is included in the shell. Wildcard expansion is *not*
                  implemented in VMS (sorry). Please mind that the -q option
                  gives a more compact listing of the file statistics.
```

# Makefiles

Makefiles have been provided for automatic build-up of the executable program
and to process a test file.
```
makefile.djc: ... make file for MSDOS port of gcc
makefile.tcc .... DOS make file, for tcc
makefile.unx .... make file for Unix machines. Set up for gcc, may be tailored
```

# Test file

The file `voice.src`, also used for testing the IS54 VSELP, is needed
for testing the sv-p56 demo programs. A reference, normalized file,
is available in the ZIP-compatible archive sv56-tst.zip. [pk]unzip is
necessary to extract the reference processed file. The contents of this
archive file is, as reported by unzip:
```
 Length  Method   Size  Ratio   Date    Time   CRC-32     Name
 ------  ------   ----  -----   ----    ----   ------     ----
 105472  Deflate  79982  24%  01-12-95  10:23  66211f99   voice.nrm
 105472  Deflate  80086  24%  08-21-95  12:25  8d3c67bf   voice.ltl
 ------          ------  ---                              -------
 210944          160068  24%                              2      
```

NOTE! This file is in the big-endian (high-byte first) format. Therefore,
      before using under MSDOS or VAX/VMS, the files need to be byte-swapped.
      See unsupported program sb in the ../unsup directory. If testing is
      done using the provided makefiles, they will attempt to carry out
      the necessary byte-swapping for voice.nrm. For this, a version of
      the utility awk (gawk is preferred) must be available in the path.

-- <simao@ctd.comsat.com> --
