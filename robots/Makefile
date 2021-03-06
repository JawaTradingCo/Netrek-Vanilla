CONFIG = system.mk

srcdir = .

include ../$(CONFIG)

INSTALL = /usr/bin/install -c
INSTALLPROG = ${INSTALL}
INSTALLDATA = ${INSTALL} -m 644

CFLAGS = $(EXTRAINCS) $(FLAGS) -DROBOT -I. -I../include

LIBS = $(EXTRALIBS)

TOOLDIR= $(LIBDIR)/tools

LINTFLAGS = -habxc $(EXTRAINCS) $(FLAGS)

C_OBJS = $(RANDOMO) roboshar.o ../ntserv/libnetrek.a

SRCS = ${srcdir}/puck.c ${srcdir}/puckmove.c \
	${srcdir}/mars.c ${srcdir}/marsmove.c \
	${srcdir}/robotII.c ${srcdir}/rmove.c \
	$(RANDOMC) ${srcdir}/../ntserv/commands.c \
	${srcdir}/basep.c \
	${srcdir}/newbie.c \
	${srcdir}/inl.c ${srcdir}/inlcomm.c ${srcdir}/inlcmds.c \
	${srcdir}/pret.c

EXECS =	puck mars robotII basep newbie inl pret

all: $(PMAKE) $(EXECS)

PUCK_OBJS = puck.o puckmove.o commands_puck.o $(C_OBJS)
puck: $(PMAKE) $(PUCK_OBJS)
	$(CC) $(CFLAGS)  ${LDFLAGS} -o puck $(PUCK_OBJS) $(EXTRALIBS)

M_OBJS = mars.o marsmove.o commands_mars.o $(C_OBJS)
mars: $(PMAKE) $(M_OBJS)
	$(CC) $(CFLAGS)  ${LDFLAGS} -o mars $(M_OBJS) $(EXTRALIBS)

R_OBJS = robotII.o rmove.o commands.o $(C_OBJS)
robotII: $(PMAKE) $(R_OBJS)
	$(CC) $(CFLAGS)  ${LDFLAGS} -o robotII  $(R_OBJS) $(EXTRALIBS)

B_OBJS = basep.o commands_basep.o $(C_OBJS)  
basep: $(PMAKE) $(B_OBJS)
	$(CC) $(CFLAGS)  ${LDFLAGS} -o basep $(B_OBJS) $(EXTRALIBS)

N_OBJS = newbie.o commands_newbie.o $(C_OBJS)
newbie: $(PMAKE) $(N_OBJS)
	$(CC) $(CFLAGS)  ${LDFLAGS} -o newbie $(N_OBJS) $(EXTRALIBS)

P_OBJS = pret.o commands_pret.o $(C_OBJS)
pret: $(PMAKE) $(P_OBJS)
	$(CC) $(CFLAGS)  ${LDFLAGS} -o pret $(P_OBJS) $(EXTRALIBS)

I_OBJS = inl.o inlcomm.o inlcmds.o $(C_OBJS)
inl: $(PMAKE) $(I_OBJS)
	$(CC) $(CFLAGS)  ${LDFLAGS} -o inl $(I_OBJS) $(EXTRALIBS)

commands_mars.o: $(PMAKE) ${srcdir}/../ntserv/commands.c
	$(CC) $(CFLAGS) $(DEP) -DDOG -c ${srcdir}/../ntserv/commands.c -o commands_mars.o

commands_puck.o: $(PMAKE) ${srcdir}/../ntserv/commands.c
	$(CC) $(CFLAGS) $(DEP) -DPUCK -c ${srcdir}/../ntserv/commands.c -o commands_puck.o

commands.o: $(PMAKE) ${srcdir}/../ntserv/commands.c
	$(CC) $(CFLAGS) $(DEP) -c ${srcdir}/../ntserv/commands.c -o commands.o

commands_basep.o: $(PMAKE) ${srcdir}/../ntserv/commands.c
	$(CC) $(CFLAGS) $(DEP) -DBASEP -c ${srcdir}/../ntserv/commands.c -o commands_basep.o

commands_newbie.o: $(PMAKE) ${srcdir}/../ntserv/commands.c
	$(CC) $(CFLAGS) $(DEP) -DNEWBIE -c ${srcdir}/../ntserv/commands.c -o commands_newbie.o

commands_pret.o: $(PMAKE) ${srcdir}/../ntserv/commands.c
	$(CC) $(CFLAGS) $(DEP) -DPRET -c ${srcdir}/../ntserv/commands.c -o commands_pret.o

clean:: 
	@rm -f *.o *.ln

reallyclean:: clean
	@rm -f $(EXECS) *~ #*# .depend


install: $(EXECS) 
	$(INSTALLPROG) $(INSTALLOPTS) puck $(DESTDIR)$(LIBDIR)/puck
	$(INSTALLPROG) $(INSTALLOPTS) mars $(DESTDIR)$(LIBDIR)/mars
	$(INSTALLPROG) $(INSTALLOPTS) robotII $(DESTDIR)$(LIBDIR)/robotII
	$(INSTALLPROG) $(INSTALLOPTS) basep $(DESTDIR)$(LIBDIR)/basep
	$(INSTALLPROG) $(INSTALLOPTS) newbie $(DESTDIR)$(LIBDIR)/newbie
	$(INSTALLPROG) $(INSTALLOPTS) pret $(DESTDIR)$(LIBDIR)/pret
	$(INSTALLPROG) $(INSTALLOPTS) inl $(DESTDIR)$(LIBDIR)/inl
	$(INSTALLPROG) $(INSTALLOPTS) ${srcdir}/end_tourney.pl $(DESTDIR)$(LIBDIR)/end_tourney.pl
	$(INSTALLPROG) $(INSTALLOPTS) ${srcdir}/auto-archive.pl $(DESTDIR)$(LIBDIR)/auto-archive.pl

lint: $(SRCS)
	lint $(LINTFLAGS) -u $?
	touch lint

rmdependencies:
	rm -f .depend

depend::
	touch .depend
	${CC} -M $(CFLAGS) $(SRCS) > .depend

tags::
	@etags $(SRCS)

sinclude .depend
# DO NOT DELETE
