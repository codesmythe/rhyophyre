CC=zcc +cpm
CFLAGS := -Wall -Werror -DDEBUG=1
#CFLAGS := -Wall -DDEBUG=1
OFLAG=-O2

all: KOCH.COM D7220.COM SHOWPCX.COM TEXT.COM

KOCH.COM: koch.o gdc7220.o
	$(CC) $(CFLAGS) $(OFLAG) koch.o gdc7220.o -o koch -lmath48 -create-app

D7220.COM: d7220.o gdc7220.o
	$(CC) $(CFLAGS) $(OFLAG) d7220.o gdc7220.o -o d7220 -create-app

# Handle hbios.asm
SHOWPCX.COM: showpcx.o pcx.o gdc7220.o dma.o hbios.o hbios_asm.o
	$(CC) $(CFLAGS) $(OFLAG)  showpcx.o pcx.o gdc7220.o dma.o hbios.o hbios_asm.o -o showpcx -create-app

TEXT.COM: text.o gdc7220.o
	$(CC) $(CFLAGS) $(OFLAG) text.o gdc7220.o -o text -create-app

gdc7220.o: gdc7220.c gdc7220.h rhyophyre.h font7220.h
koch.o: koch.c gdc7220.h
d7220.o: d7220.c gdc7220.h
showpcx.o: showpcx.c pcx.h gdc7220.h hbios.h dma.h
pcx.o: pcx.c pcx.h gdc7220.h
text.o: text.c gdc7220.h

hbios_asm.o: hbios.asm
	$(CC) $(CFLAGS) -o hbios_asm.o -c hbios.asm

clean:
	rm -f *.o *.lis *.map koch KOCH.COM d7220 D7220.COM showpcx SHOWPCX.COM text TEXT.COM
