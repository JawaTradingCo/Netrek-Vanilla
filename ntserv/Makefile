
srcdir = .

CONFIG = system.mk
RANLIB = ranlib
RANLIB_FLAGS = 

include ../$(CONFIG)

INSTALL = /usr/bin/install -c
INSTALLPROG = ${INSTALL}
INSTALLDATA = ${INSTALL} -m 644

#	libnetrek object files

L_OBJS = advertise.o alarm.o balance.o bans.o bay.o blog.o \
	coup.o \
	data.o db.o detonate.o distress.o draft.o \
	enter.o \
	feature.o \
	gencmds.o genspkt.o getpath.o getship.o glog.o \
	interface.o ip.o \
	ltd_stats.o \
	openmem.o orbit.o \
	phaser.o ping.o planet.o plasma.o \
	rsa_key.o reserved.o \
	salt.o slotmaint.o sigpipe.o sintab.o smessage.o socket.o solicit.o \
	startrobot.o sturgeon.o sysdefaults.o \
	torp.o transwarp.o \
	util.o \
	warning.o

#	ntserv object files

R_OBJS =    cluecheck.o death.o \
	    findslot.o getentry.o getname.o input.o \
	    main.o redraw.o \
	    reserved.o  \
	    timecheck.o  \
	    $(RANDOMO) $(STRDUPO) \
	    ntscmds.o \
	    queue.o libnetrek.a


#	daemon object files

D_OBJS =    daemon.o \
	    $(RANDOMO) queue.o \
	    wander2.o solicit.o conquer.o \
	    libnetrek.a

#	Src files

R_FILES =   ${srcdir}/cluecheck.c ${srcdir}/coup.c ${srcdir}/data.c \
            ${srcdir}/db.c \
            ${srcdir}/death.c ${srcdir}/detonate.c  ${srcdir}/enter.c \
	    ${srcdir}/findslot.c  ${srcdir}/getentry.c \
            ${srcdir}/getname.c  ${srcdir}/salt.c ${srcdir}/getship.c  ${srcdir}/input.c \
	    ${srcdir}/interface.c  ${srcdir}/main.c  ${srcdir}/orbit.c \
            ${srcdir}/phaser.c  ${srcdir}/plasma.c \
	    ${srcdir}/redraw.c  ${srcdir}/reserved.c  ${srcdir}/sintab.c \
            ${srcdir}/socket.c  ${srcdir}/genspkt.c  ${srcdir}/smessage.c \
	    ${srcdir}/startrobot.c  ${srcdir}/timecheck.c \
            ${srcdir}/torp.c  ${srcdir}/util.c  ${srcdir}/warning.c \
	    $(RANDOMC)  ${srcdir}/ping.c ${srcdir}/getpath.c $(STRDUPC) \
            ${srcdir}/distress.c ${srcdir}/transwarp.c \
            ${srcdir}/gencmds.c ${srcdir}/ntscmds.c ${srcdir}/openmem.c \
            ${srcdir}/feature.c ${srcdir}/queue.c ${srcdir}/slotmaint.c \
            ${srcdir}/wander2.c ${srcdir}/sysdefaults.c ${srcdir}/rsa_key.c

SRC = 	    $(R_FILES)  data.h  defs.h planets.h  struct.h \
	    packets.h  copyright.h

LIBS = $(RSA_LIB) $(EXTRALIBS)

INCS = $(RSA_INCS) $(EXTRAINCS) -I../include

CFLAGS = $(FLAGS) $(INCS)

LINTFLAGS = -habxc $(INCS)


all: $(PMAKE) ntserv daemon

ntserv: $(PMAKE) $(R_OBJS)
	$(CC) $(CFLAGS) ${LDFLAGS} -o ntserv $(R_OBJS) $(LIBS) $(LIBCRYPT) -lgdbm

daemon: $(PMAKE) $(D_OBJS)
	$(CC) $(CFLAGS) ${LDFLAGS} -o daemon $(D_OBJS) $(EXTRALIBS)

libnetrek.a: $(L_OBJS)
	$(AR) cru $@ $(L_OBJS)
	$(RANLIB) $(RANLIB_FLAGS) $@

libnetrek.so: $(L_OBJS)
	$(CC) -shared -Wl,-soname,$@ -o $@ $(L_OBJS) -lc

commands.o: $(PMAKE) ${srcdir}/commands.c
	$(CC) $(CFLAGS) $(DEP) -c ${srcdir}/commands.c

db.o: $(PMAKE) db.c
	$(CC) $(CFLAGS) $(DEP) -c db.c

cflags:
	echo "static char cflags[]=\"$(CFLAGS) $(LIBS)\";" >../cflags.h

lint: $(SRC)
	lint $(LINTFLAGS) -u $?
	touch lint

lintall: $(SRC)
	ling $(LINTFLAGS) $(SRC)

clean: rmdependencies
	/bin/rm -f *.a *.o *.ln make.out core

reallyclean:  clean
	rm -f ntserv daemon .motd *~ #*#

uninstall:
	-cd $(XTREKDIR); rm -f daemon .motd .sysdef; rm -rf slots
	-cd $(LIBDIR); rm -f ntserv ; rm -rf slots

install: ntserv daemon
	mkdir -p $(DESTDIR)$(LIBDIR) $(DESTDIR)$(LOCALSTATEDIR)
	$(INSTALLPROG) $(INSTALLOPTS) ntserv $(DESTDIR)$(LIBDIR)/ntserv
	$(INSTALLPROG) $(INSTALLOPTS) daemon $(DESTDIR)$(LIBDIR)/daemon

install-ntserv: ntserv
	mkdir -p $(DESTDIR)$(LIBDIR)/ntserv-archive
	mv $(DESTDIR)$(LIBDIR)/ntserv $(DESTDIR)$(LIBDIR)/ntserv-archive/ntserv.`date +%Y-%m-%d`.$$
	$(INSTALLPROG) $(INSTALLOPTS) ntserv $(DESTDIR)$(LIBDIR)/ntserv

install-daemon: daemon
	mkdir -p $(DESTDIR)$(LIBDIR)/daemon-archive
	mv $(DESTDIR)$(LIBDIR)/daemon $(DESTDIR)$(LIBDIR)/daemon-archive/daemon.`date +%Y-%m-%d`.$$
	$(INSTALLPROG) $(INSTALLOPTS) daemon $(DESTDIR)$(LIBDIR)/daemon

installbin: install
	echo "target installbin deprecated, assumed install"

depend::
	${CC} -M $(CFLAGS) $(R_FILES) > .depend

rmdependencies:
	rm -f .depend

ctags:
	ctags $(SRC)

tags::
	@etags $(SRC)

# Note: on systems that are not using GNU make, the following line
# will likely trigger an error.  Work around this by using GNU make
# from the command line.
sinclude .depend
# DO NOT DELETE THIS LINE -- make depend depends on it.
