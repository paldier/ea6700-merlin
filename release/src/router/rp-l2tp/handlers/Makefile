# Generated automatically from Makefile.in by configure.
# $Id: Makefile.in 3323 2011-09-21 18:45:48Z lly.dev $
# Makefile for LNS handlers
# LIC: GPL

prefix=/usr
exec_prefix=${prefix}
mandir=${prefix}/man
docdir=/usr/doc/l2tp-$(VERSION)
install=/usr/bin/install -c
install_dir=/usr/bin/install -c -d
sbindir=${exec_prefix}/sbin

HANDLERS=sync-pppd.so cmd.so

OBJS=pty.o sync-pppd.o dstring.o
SRCS=$(OBJS:.o=.c)
CFLAGS=-O2 -Wall -DLINUX26 -DCONFIG_BCMWL5 -DDEBUG_NOISY -DDEBUG_RCTEST -pipe -DBCMWPA2 -DBCMARM -fno-strict-aliasing -marm -DRTCONFIG_NVRAM_64K -DLINUX_KERNEL_VERSION=132644  -idirafter /home/paldier/68u/release/src-rt-6.x.4708/linux/linux-2.6.36/include -I.. -I../libevent -I. -Wall

all: $(HANDLERS) l2tp-control

l2tp-control: cmd-control.o
	arm-brcm-linux-uclibcgnueabi-gcc -o l2tp-control cmd-control.o

cmd-control.o: cmd-control.c
	arm-brcm-linux-uclibcgnueabi-gcc $(CFLAGS) -c -o $@ $^

%.o: %.c
	arm-brcm-linux-uclibcgnueabi-gcc $(CFLAGS) -fPIC -c -o $@ $<

sync-pppd.so: pty.o sync-pppd.o
	arm-brcm-linux-uclibcgnueabi-gcc -shared -o $@ $^

cmd.so: cmd.o dstring.o
	arm-brcm-linux-uclibcgnueabi-gcc -shared -o $@ $^

clean:
	rm -f *.so *.o *~
	rm -f l2tp-control

install: all
	-mkdir -p $(RPM_INSTALL_ROOT)$(sbindir)
	-mkdir -p $(RPM_INSTALL_ROOT)$(prefix)/lib/l2tp/plugins
	$(install) -m 755 -s l2tp-control $(RPM_INSTALL_ROOT)$(sbindir)
	$(install) -m 755 $(HANDLERS) $(RPM_INSTALL_ROOT)$(prefix)/lib/l2tp/plugins

distclean: clean
	rm -f Makefile
