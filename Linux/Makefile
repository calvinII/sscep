#
# Makefile for Linux
#

BINDIR = /opt/CertNanny/bin
MANDIR = /usr/local/man/man8

CC	= gcc
#WITH_DEBUG   = -g
OPENSSL_INCLUDE = /usr/include/openssl
OPENSSL_LIB = /usr/lib/x86_64-linux-gnu
CFLAGS	= -Wall -O $(WITH_DEBUG) -I $(OPENSSL_INCLUDE)

LDFLAGS = -L$(OPENSSL_INCLUDE)
LDLIBS = -lcrypto

MAN	= sscep.8
PROG	= sscep
OBJS    = sscep.o init.o net.o sceputils.o pkcs7.o ias.o fileutils.o configuration.o engine.o

all: $(PROG)_static $(PROG)_dyn

$(PROG)_static: $(OBJS)
	$(CC) $(CFLAGS) -o $(PROG)_static $(OBJS) $(OPENSSL_LIB)/libcrypto.a -ldl

$(PROG)_dyn: $(OBJS)
	$(CC) $(CFLAGS) -o $(PROG)_dyn $(OBJS) $(LDLIBS) $(LDFLAGS)

clean:
	rm -f $(PROG) $(OBJS) $(MAN) core

install:
	echo "TODO: install target"

package: all
	echo "Creating package..."
	Linux/make_Linux_package.sh

