CC = riscv64-unknown-elf-gcc
CFLAGS = -mcmodel=medany -static -nostdlib -c

all: crt.o syscalls.o

crt.o: crt.S
	$(CC) $(CFLAGS) crt.S -o crt.o

syscalls.o: syscalls.c
	$(CC) $(CFLAGS) syscalls.c -o syscalls.o

.PHONY: clean
clean:
	rm -f *.o
