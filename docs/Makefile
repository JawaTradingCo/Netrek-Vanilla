#
#	Only change CONFIG to the right .mk file.
#

VAPTH = .
srcdir = .

CONFIG = ../system.mk

#
#	Do Not Edit below here. Everything should be setup in the config
#

include $(CONFIG)

INSTALL = /usr/bin/install -c
INSTALLPROG = ${INSTALL}
INSTALLDATA = ${INSTALL} -m 644

DOCS = ${srcdir}/sample_features ${srcdir}/sample_motdclue \
	sample_sysdef ${srcdir}/sample_motd ${srcdir}/sample_ports \
	${srcdir}/sample_time ${srcdir}/sample_motdbasep \
	${srcdir}/sample_reserved ${srcdir}/sample_tourn.map

install: $(DOCS)
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/features ]; then \
		$(INSTALLDATA) ${srcdir}/sample_features	$(DESTDIR)$(SYSCONFDIR)/features ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/motd_clue ]; then \
		$(INSTALLDATA) ${srcdir}/sample_motdclue	$(DESTDIR)$(SYSCONFDIR)/motd_clue ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/motd_clue_logo.MASTER ]; then \
		$(INSTALLDATA) ${srcdir}/sample_motdclue	$(DESTDIR)$(SYSCONFDIR)/motd_clue_logo.MASTER ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/motd_basep_logo.MASTER ]; then \
		$(INSTALLDATA) ${srcdir}/sample_motdbasep	$(DESTDIR)$(SYSCONFDIR)/motd_basep_logo.MASTER ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/sysdef ]; then \
		$(INSTALLDATA) sample_sysdef	$(DESTDIR)$(SYSCONFDIR)/sysdef ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/motd ]; then \
		$(INSTALLDATA) ${srcdir}/sample_motd	$(DESTDIR)$(SYSCONFDIR)/motd ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/motd_logo.MASTER ]; then \
		$(INSTALLDATA) ${srcdir}/sample_motd	$(DESTDIR)$(SYSCONFDIR)/motd_logo.MASTER ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/ports ]; then \
		$(INSTALLDATA) ${srcdir}/sample_ports	$(DESTDIR)$(SYSCONFDIR)/ports ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/time ]; then \
		$(INSTALLDATA) ${srcdir}/sample_time	$(DESTDIR)$(SYSCONFDIR)/time ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/motd_basep ]; then \
		$(INSTALLDATA) ${srcdir}/sample_motdbasep	$(DESTDIR)$(SYSCONFDIR)/motd_basep ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/reserved ]; then \
		$(INSTALLDATA) ${srcdir}/sample_reserved	$(DESTDIR)$(SYSCONFDIR)/reserved ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/tourn.map ]; then \
		$(INSTALLDATA) ${srcdir}/sample_tourn.map	$(DESTDIR)$(SYSCONFDIR)/tourn.map ; \
	fi
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/comment ]; then \
		$(INSTALLDATA) ${srcdir}/sample_comment		$(DESTDIR)$(SYSCONFDIR)/comment ; \
	fi
	touch $(DESTDIR)$(SYSCONFDIR)/nocount
	touch $(DESTDIR)$(SYSCONFDIR)/banned
	touch $(DESTDIR)$(SYSCONFDIR)/bypass
	touch $(DESTDIR)$(SYSCONFDIR)/clue-bypass
	if [ ! -f $(DESTDIR)$(SYSCONFDIR)/blosxom.conf ]; then \
		$(INSTALLDATA) ${srcdir}/sample_blosxom.conf		$(DESTDIR)$(SYSCONFDIR)/blosxom.conf ; \
	fi
	mkdir -p $(DESTDIR)$(SYSCONFDIR)/ip/duplicates
	mkdir -p $(DESTDIR)$(SYSCONFDIR)/ip/whitelist
	mkdir -p $(DESTDIR)$(SYSCONFDIR)/ip/hide
	mkdir -p $(DESTDIR)$(SYSCONFDIR)/ip/mute
	mkdir -p $(DESTDIR)$(SYSCONFDIR)/ip/muteall
	mkdir -p $(DESTDIR)$(SYSCONFDIR)/ip/ignore
	mkdir -p $(DESTDIR)$(SYSCONFDIR)/ip/deny
	mkdir -p $(DESTDIR)$(LOCALSTATEDIR)/ip/ignore/doosh
	mkdir -p $(DESTDIR)$(LOCALSTATEDIR)/ip/ignore/multi
	mkdir -p $(DESTDIR)$(LOCALSTATEDIR)/ip/ignore/by-ip
