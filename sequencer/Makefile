# Change CONFIG to the .mk file that matches your system

CONFIG = system.mk

srcdir = .

# Do Not Change anything below this line. It should be setup in config

include ../$(CONFIG)

INSTALL = /usr/bin/install -c
INSTALLPROG = ${INSTALL}
INSTALLDATA = ${INSTALL} -m 644

# this is for revised ntserv/struct.h

CFLAGS = $(EXTRAINCS) $(FLAGS) -I../include

LIBS = $(EXTRALIBS)

TOOLDIR = $(LIBDIR)/tools

LINTFLAGS = -habxc $(EXTRAINCS) $(FLAGS)

#	Common Objects

C_OBJS = roboshar.o ../ntserv/libnetrek.a

#	Sequencer Objects

S_OBJS = sequencer.o commands_sequencer.o $(C_OBJS) ../ntserv/libnetrek.a

SRCS = ${srcdir}/roboshar.c ${srcdir}/sequencer.c

EXECS =	sequencer 

all: $(PMAKE) $(EXECS)

sequencer: $(PMAKE) $(S_OBJS)
	$(CC) $(CFLAGS)  ${LDFLAGS} -o sequencer $(S_OBJS) $(LIBS)

commands_sequencer.o: $(PMAKE) ${srcdir}/../ntserv/commands.c
	$(CC) $(CFLAGS) $(DEP) -DSEQUENCER -c ${srcdir}/../ntserv/commands.c -o commands_sequencer.o

install: $(EXECS) 
	$(INSTALLPROG) $(INSTALLOPTS) sequencer $(DESTDIR)$(LIBDIR)/sequencer

lint: $(SRCS)
	lint $(LINTFLAGS) -u $?
	touch lint

depend::
	${CC} -M $(CFLAGS) $(SRCS) > .depend

etags::
	@etags $(SRCS)

clean:: 
	@rm -f *.o *.ln

reallyclean:: clean
	@rm -f $(EXECS) *~ #*# .depends

rmdependencies:
	rm -f .depend

sinclude .depend
# DO NOT DELETE
