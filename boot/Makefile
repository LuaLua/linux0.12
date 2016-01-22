

LDFLAGS	+= -Ttext=0

all: bootsect.bin floppya.img
	dd if=bootsect.bin bs=512 count=1 of=floppya.img conv=notrunc

bootsect.bin: bootsect.s
	as --32 -o bootsect.o bootsect.s
	ld -Ttext=0 -m elf_i386 -o bootsect.elf bootsect.o 
	objcopy -j .text -O binary bootsect.elf bootsect.bin

floppya.img:
	dd if=/dev/zero of=floppya.img bs=512 count=2880

clean:
	rm -f bootsect.bin bootsect.o bootsect.elf floppya.img bochsout.txt
