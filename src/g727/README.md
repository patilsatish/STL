       ==============================================================
       COPYRIGHT NOTE: This software  module  was  developed  by The
       Ukranian Scientific Institute of Communication (Ministry of
       Communication), who holds the copyrights of the implementation
       and its *use* was granted as per the Terms in ITU-T Rec.G.191.

       This module, and all of its  derivations,  is subject  to  the
       "ITU-T General Public License".  Please have it  read  in  the
       distribution disk, or in the ITU-T Recommendation G.191 on
       "SOFTWARE TOOLS FOR SPEECH AND AUDIO CODING STANDARDS".
       ==============================================================


The UGST G727 module, version 1.01 (04.Aug.97) consists of the
following files:

# General

    porttest.rme:  Readme file (in g727-tst.zip) with brief description of
                   portability test files.

# C program code

    g727.c ......... user entry-level function definition
    g727.h ......... prototypes for the user

# Demo

    g727demo.c ..... demo program for the encoder and decoder
    ugstdemo.h ..... prototypes and definitions needed by UGST demo programs.
                     Available in other directory.
    discard.c ...... Program to discard LSB bits in ADPCM samples. The
                     program simulates the reduction of packets in the
                     overloading condition in the network. NOTE: This
                     program is in its original form and its I/O has not
                     yet been adapted to the UGST format.

The `g727demo` program can be used for testing the implementation as
well as for processing speech files.

NOTE: The original ASCII digital test sequences of ITU-T G.727 have to
      be converted in pure and raw binary format for processing (see
      `g727-tv.rme`). The test vectors have not been included in the
      UGST distribution.

# Makefiles

Makefiles have been provided for automatic build-up of the executable program
and to process the test sequences, WHEN made available by the user and left
in the subdirectory `tstvector`:

    makefile.tcc: ... make file for MSDOS Borland tcc
    makefile.djc: ... make file for MSDOS port of gcc
    makefile.unx: ... make file for Unix, using either cc, acc (Sun), or gcc

The provided makefiles can run a portability test on the demo
program. They need the archive `g727-tst.zip` ([pk]zip compatible
archive) and [pk]unzip to extract the proper source and reference
processed files. The archive g727-tst.zip contains data in big endian
format and need to be byte-swapped in little-endian systems (e.g. PC &
Digital platforms). Conversion is automatically (hopefully) performed
by the makefile test code.


# Compliance Testing

The original C code provided by the PTT Ukraine was originally tested
on the following platforms:

- IBM PC, MS-DOS. Compilers: Microsoft Visual C++ 1.0,
  Zortech C++ 3.0, Borland C++ 3.1.
- IBM PC, OS/2 Warp. Compiler - Watcom C++ 10.0.
- DEC Alpha 2000 AXP, DEC OSF/1 Unix. Compiler - GNU C.

UGST version tested:
- Simao Campos - COMSAT <simao.campos@comsat.com>
```
    Platform:	HP 9000-700
    OS:		HPUX 9.05
    Compiler:	GNU gcc
    Platform:	PC
    OS:		MSDOS 5.0
    Compiler:	GNU gcc V.2.6.3 (DJGPP), Borland TurboC++ V.1.0
```

- Morgan Lindqvist ERA/T/VA <Morgan.Lindqvist@era-t.ericsson.se>
```
  Platform:	Digital Alpha 500
  OS:		Digital UNIX 4.0
  Compiler:	GNU gcc-2.7.2.1 and Digital cc V5.2-033
```
-- simao, 07.Jan.1998
