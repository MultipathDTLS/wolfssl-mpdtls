# includes append to these:
SUFFIXES =
TESTS =
CLEANFILES =
DISTCLEANFILES =
bin_PROGRAMS =
noinst_HEADERS =
lib_LTLIBRARIES =
man_MANS =
noinst_LTLIBRARIES =
noinst_PROGRAMS =
include_HEADERS =
nobase_include_HEADERS =
check_PROGRAMS =
EXTRA_HEADERS =
BUILT_SOURCES=
EXTRA_DIST=
dist_doc_DATA=
dist_noinst_SCRIPTS =
check_SCRIPTS =

#includes additional rules from aminclude.am
@INC_AMINCLUDE@
DISTCLEANFILES+= aminclude.am

CLEANFILES+= cert.der \
             cert.pem \
             certecc.der \
             certecc.pem \
             certreq.der \
             certreq.pem \
             key.der \
             key.pem \
             ntru-cert.der \
             ntru-cert.pem \
             ntru-key.raw \
             othercert.der \
             othercert.pem \
             pkcs7cert.der \
             pkcs7envelopedData.der \
             pkcs7signedData.der

exampledir = $(docdir)/example
dist_example_DATA=

ACLOCAL_AMFLAGS= -I m4

EXTRA_DIST+= lib/dummy

EXTRA_DIST+= wolfssl-ntru.vcproj
EXTRA_DIST+= wolfssl.vcproj
EXTRA_DIST+= wolfssl.vcxproj
EXTRA_DIST+= wolfssl-ntru.sln
EXTRA_DIST+= wolfssl.sln
EXTRA_DIST+= wolfssl64.sln
EXTRA_DIST+= valgrind-error.sh
EXTRA_DIST+= gencertbuf.pl
EXTRA_DIST+= IDE
EXTRA_DIST+= README.md
EXTRA_DIST+= LICENSING
EXTRA_DIST+= INSTALL

include cyassl/include.am
include wolfssl/include.am
include certs/include.am
include certs/1024/include.am
include certs/crl/include.am
include doc/include.am
include swig/include.am

include src/include.am
include support/include.am
include wolfcrypt/benchmark/include.am
include wolfcrypt/src/include.am
include wolfcrypt/test/include.am
include examples/client/include.am
include examples/server/include.am
include examples/echoclient/include.am
include examples/echoserver/include.am
include testsuite/include.am
include tests/include.am
include sslSniffer/sslSnifferTest/include.am
include rpm/include.am
include mqx/util_lib/Sources/include.am
include mqx/wolfcrypt_benchmark/Sources/include.am
include mqx/wolfcrypt_test/Sources/include.am
include mqx/wolfssl/include.am
include mqx/wolfssl_client/Sources/include.am
include mplabx/include.am
include mplabx/wolfcrypt_benchmark.X/nbproject/include.am
include mplabx/wolfcrypt_test.X/nbproject/include.am
include mplabx/wolfssl.X/nbproject/include.am
include mcapi/include.am
include mcapi/wolfcrypt_mcapi.X/nbproject/include.am
include mcapi/wolfcrypt_test.X/nbproject/include.am
include mcapi/wolfssl.X/nbproject/include.am
include mcapi/zlib.X/nbproject/include.am
include tirtos/include.am
include scripts/include.am

if USE_VALGRIND
TESTS_ENVIRONMENT=./valgrind-error.sh
endif

TEST_EXTENSIONS=.test
TESTS += $(check_PROGRAMS)

check_SCRIPTS+= $(dist_noinst_SCRIPTS)
TESTS += $(check_SCRIPTS)

test: check
tests/unit.log: testsuite/testsuite.log

DISTCLEANFILES+= cyassl-config
DISTCLEANFILES+= wolfssl-config
# fips files shouldn't be left after make distclean
DISTCLEANFILES+= ctaocrypt/src/fips.c
DISTCLEANFILES+= ctaocrypt/src/fips_test.c

maintainer-clean-local:
	-rm Makefile.in
	-rm aclocal.m4
	-rm build-aux/compile
	-rm build-aux/config.guess
	-rm build-aux/config.sub
	-rm build-aux/depcomp
	-rm build-aux/install-sh
	-rm build-aux/ltmain.sh
	-rm build-aux/missing
	-rm cyassl-config
	-rmdir build-aux
	-rm configure
	-rm config.log
	-rm config.status
	-rm config.in
	-rm m4/libtool.m4
	-rm m4/ltoptions.m4
	-rm m4/ltsugar.m4
	-rm m4/ltversion.m4
	-rm m4/lt~obsolete.m4
	-rm support/wolfssl.pc
	find . -type f -name '*~' -exec rm -f '{}' \;
	-rm -f @PACKAGE@-*.tar.gz
	-rm -f @PACKAGE@-*.rpm

# !!!! first line of rule has to start with a hard (real) tab, not spaces
egs:
	$(MAKE) examples/client/client; \
	$(MAKE) examples/echoclient/echoclient;\
	$(MAKE) examples/server/server; \
	$(MAKE) examples/echoserver/echoserver;

wc_egs:
	$(MAKE) wolfcrypt/test/testwolfcrypt; \
	$(MAKE) wolfcrypt/benchmark/benchmark;

install-exec-local:	install-generic-config

install-generic-config:
	$(mkinstalldirs) $(DESTDIR)$(bindir)
	$(INSTALL_SCRIPT) @GENERIC_CONFIG@ $(DESTDIR)$(bindir)

uninstall-local:
	-rm -f $(DESTDIR)$(bindir)/@GENERIC_CONFIG@

merge-clean:
	@find ./ | $(GREP) \.gcda | xargs rm -f
	@find ./ | $(GREP) \.gcno | xargs rm -f
	@find ./ | $(GREP) \.gz | xargs rm -f
	@find ./ | $(GREP) \.orig | xargs rm -f
	@find ./ | $(GREP) \.rej | xargs rm -f
	@find ./ | $(GREP) \.rpm | xargs rm -f
	@find ./ | $(GREP) \.THIS | xargs rm -f
	@find ./ | $(GREP) \.OTHER | xargs rm -f
	@find ./ | $(GREP) \.BASE | xargs rm -f
	@find ./ | $(GREP) \~$$ | xargs rm -f
