SRCS := ../../BBCZ80/DIST.asm ../../BBCZ80/MAIN.asm ../../BBCZ80/EXEC.asm ../../BBCZ80/EVAL.asm ../../BBCZ80/ASMB.asm ../../BBCZ80/CMOS.asm ../../BBCZ80/MATH.asm ../../BBCZ80/HOOK.asm MSXBIOS.asm ../../BBCZ80/DATA.asm

# system agnostic commands
ifdef ComSpec
	RMF	:= del /f /q
	SEARCH	:= find
	CP	:= copy /b
	MODE := MOVE
	/	:= $(strip \)
else
	RMF	:= rm -f 
	SEARCH	:= grep
	CP	:= cp
	/	:= /
endif 

bbcbasic.com: $(SRCS)
	@echo Assembling MSX edition..
	z88dk-z80asm  -Oobj -obbcbasic.com -b -d -l -m $(SRCS)
	$(CP) obj$/bbcbasic.com bin$/BBCBASIC.com
	$(RMF) obj$/bbcbasic.com
	@echo done

clean:
	$(RMF) obj$/*
	@echo Cleanup done