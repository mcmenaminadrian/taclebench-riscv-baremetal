
CC = riscv64-unknown-elf-gcc
src = $(wildcard *.c)
obj = $(src:.c=.o)
REMDIR = ../../../riscv-common
MCMODEL = -mcmodel=medany
CFLAGS = -mcmodel=medany -static -nostdlib -fno-builtin-printf -fno-common -T$(REMDIR)/test.ld
OBJFILES = crt.o syscalls.o

all: others exec

others:
	echo 'Building crt and syscalls'
	$(MAKE) -C $(REMDIR)
	cp $(REMDIR)/*.o .

exec: $(obj) $(OBJFILES)
	$(CC) $(CFLAGS) $(OBJFILES) $(obj) -o $(patsubst %.o, %, $<).exe

exec.o: $(src)
	$(CC) $(MCMODEL) -c $(src) -o $@

.PHONY: clean
clean:
	rm -f $(REMDIR)/*.o *.o *.exe

