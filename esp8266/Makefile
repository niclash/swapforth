CC = xtensa-lx106-elf-gcc
AS = xtensa-lx106-elf-as
ASFLAGS = -Wa,-a=lst
CFLAGS = -Os -I. -mlongcalls
LDLIBS = -nostdlib -Wl,--start-group -lmain -lnet80211 -lwpa -llwip -lpp -lphy -Wl,--end-group -lgcc
LDFLAGS = -Tswapforth.ld

swapforth-0x00000.bin: swapforth
	esptool.py elf2image $^

swapforth: swapforth.o nuc.o

flash: swapforth-0x00000.bin
	esptool.py write_flash 0 swapforth-0x00000.bin 0x40000 swapforth-0x40000.bin

clean:
	rm -f *.o swapforth *.bin
