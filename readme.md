Create object file from kernel.asm and kernel.c and then link it using our linker script.

`nasm -f elf32 kernel.asm -o kasm.o`

Will run the assembler to create the object file kasm.o in ELF-32 bit format:

`gcc -m32 -c kernel.c -o kc.o`

The -c option makes sure that after compiling, linking doesn't implicitly happens:


`ld -m elf_i386 -T link.ld -o kernel kasm.o kc.o`

Will run the linker with our linker script and generate the executable.

`qemu-system-i386 -kernel kernel`

Will load the kernel in the QEMU emulator
