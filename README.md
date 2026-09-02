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

Note that the name 'BBC BASIC' is used by permission of the British Broadcasting Corporation
and is not transferrable to a derived or forked work.

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
│   ├── MSXOS.asm
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



