cfgdir = $(datadir)/vyatta-cfg/templates
opdir = $(datadir)/vyatta-op/templates
networkdir = $(datadir)/ppp/network

cpiop = find  . ! -regex '\(.*~\|.*\.bak\|.*\.swp\|.*\#.*\#\)' -print0 | \
	cpio -0pd

install-exec-hook:
	mkdir -p $(DESTDIR)$(networkdir)
	cp scripts/att $(DESTDIR)$(networkdir)/
	cp scripts/verizon $(DESTDIR)$(networkdir)/
	cp scripts/sc1 $(DESTDIR)$(networkdir)/
	mkdir -p $(DESTDIR)/etc/ppp/ip-pre-up.d \
	         $(DESTDIR)/etc/ppp/ip-up.d \
	         $(DESTDIR)/etc/ppp/ip-down.d
	cp scripts/rename-wirelessmodem $(DESTDIR)/etc/ppp/ip-pre-up.d/0003rename-wirelessmodem
	chmod 755 $(DESTDIR)/etc/ppp/ip-pre-up.d/0003rename-wirelessmodem
	cp scripts/wirelessmodem.up $(DESTDIR)/etc/ppp/ip-up.d/wirelessmodem
	cp scripts/wirelessmodem.down $(DESTDIR)/etc/ppp/ip-down.d/wirelessmodem
	chmod 755 $(DESTDIR)/etc/ppp/ip-up.d/wirelessmodem
	chmod 755 $(DESTDIR)/etc/ppp/ip-down.d/wirelessmodem
	mkdir -p $(DESTDIR)$(cfgdir)
	cd templates-cfg; $(cpiop) $(DESTDIR)$(cfgdir)
	mkdir -p $(DESTDIR)$(opdir)
	cd templates-op; $(cpiop) $(DESTDIR)$(opdir)
