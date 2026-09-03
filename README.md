# BBC-BASIC for MSX
BBC BASIC (Z80) v5 is an implementation of the BBC BASIC programming language for the Z80 CPU.
It is largely compatible with Acorn's ARM BASIC V but with a few language extensions based on
features of 'BBC BASIC for Windows' and 'BBC BASIC for SDL 2.0'.  These extensions include the
EXIT statement, the address-of operator (^) and byte (unsigned 8-bit) variables and arrays
(& suffix character).

More details of the features added in version 5.00 can be found in the file WHATSNEW.TXT.

![Architecture](https://www.bbcbasic.co.uk/bbcbasic/z80arch.png)

The files in green constitute the generic BBC BASIC interpreter which is shared by all the
editions, it (just!) fits in 16 Kbytes so could be held in a ROM of this size.  The files in
the blue box are used to build the generic CP/M edition.  The files in the red box are used
to build the Acorn Z80 Second Processor edition.

On the BBC Micro, the operating-system component is known as the MOS
(Machine Operating System).  This project uses `MSXMOS.asm` for the corresponding
MSX-specific operating-system interface.
Routine names such as `OSINIT`, `OSLOAD`, `OSSAVE`, and `OSBGET` originate from
the MOS system-call interface used by the BBC Micro versions of BBC BASIC.  The
MSX implementation keeps these names as the operating-system abstraction layer,
while connecting them to the appropriate MSX-DOS and MSX BIOS services.

Note that the name 'BBC BASIC' is used by permission of the British Broadcasting Corporation
and is not transferrable to a derived or forked work.

# MSX-DOS2 Subdirectory Support

On MSX-DOS2, `LOAD`, `*LOAD`, and program loading through `CHAIN` or `RUN` can
access files in subdirectories. Use an MSX-DOS path in the filename, for example:

```basic
LOAD "SUBDIR\\PROGRAM"
*LOAD SUBDIR\\PROGRAM
```

The MSX-DOS2 build opens these files through DOS2 file handles. The existing
FCB-based implementation is retained for MSX-DOS1 and CP/M-compatible systems.
Other file commands, including `OPENIN`, `OPENOUT`, `OPENUP`, and `SAVE`, still
use the legacy FCB path and do not yet provide subdirectory support.

# Repository Structure

```text
MSX_BBC-BASIC/
├── .git/                     # Git metadata
├── .gitignore                # Git ignore rules
├── BBCZ80/                   # Z80 source assembly files for the BBC BASIC for MSX 
│   ├── ASMB.asm
│   ├── CMOS.asm
│   ├── DATA.asm
│   ├── DIST.asm
│   ├── EVAL.asm
│   ├── EXEC.asm
│   ├── HOOK.asm
│   ├── MAIN.asm
│   ├── MATH.asm
│   └── ...
├── bin/                      # Built executables for target platforms
│   ├── acorn/
│   │   ├── BBCBASIC.COM
│   │   └── MAKE.SUB
│   └── cpm/
│       ├── BBCBASIC.COM
│       └── MAKE.SUB
├── msx/                      # MSX-specific build files and generated outputs
│   ├── Makefile
│   ├── MSXBIOS.asm
│   ├── MSXMOS.asm
│   ├── BBCZ80/
│   │   ├── ASMB.lis
│   │   ├── DATA.lis
│   │   ├── DIST.lis
│   │   ├── EVAL.lis
│   │   ├── EXEC.lis
│   │   ├── HOOK.lis
│   │   ├── MAIN.lis
│   │   └── MATH.lis
│   ├── bin/
│   │   └── BBCBASIC.com
│   └── obj/
│       ├── MSXBIOS.lis
│       └── MSXOS.lis
├── src/                      # Legacy original Z80 sources; excluded from active analysis/build
│   ├── ACORN.Z80
│   ├── AMOS.Z80
│   ├── ASMB.Z80
│   ├── CMOS.Z80
│   ├── DATA.Z80
│   ├── DIST.Z80
│   ├── EVAL.Z80
│   ├── EXEC.Z80
│   ├── HOOK.Z80
│   ├── MAIN.Z80
│   ├── MATH.Z80
│   └── ... (all .Z80 legacy sources excluded from current analysis)
├── tests/                    # BASIC test scripts
│   ├── ALLTESTS.BBC
│   ├── ARRAYTST.BBC
│   ├── BYREFTST.BBC
│   ├── ERRORTST.BBC
│   ├── EXITTEST.BBC
│   ├── FILETEST.BBC
│   ├── FORTEST.BBC
│   ├── INT32TST.BBC
│   └── SLICETST.BBC
├── tools/
│   └── dev.bat
├── licence.txt
├── README.md
├── WHATSNEW.TXT
├── z88asm_option.txt
├── zcc_option.txt
└── ...
```

# Howto Compile

## Need Product: 

 Nmake 

 Z88DK (`D:\Tool\z88dk`)

The MSX build uses `z88dk-z80asm` and `z88dk-appmake`. Add the Z88DK `bin`
directory to `PATH` before running `make`:

```powershell
$env:Path = "D:\Tool\z88dk\bin;$env:Path"
```

## Compoile Command : 

 tools/dev.bat

```powershell
Set-Location msx
make
```



