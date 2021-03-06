README
======

xping is a simple PING program continiously probing multiple hosts
using ICMP-ECHO. As packets are received dots are printed on the screen.
Hosts not responding before next packet is due will get a questionmark
in the display:

           192.0.2.1 .....................................
           192.0.2.2 ????.????????????.???.?.?............
           192.0.2.3 .....................................
           192.0.2.4 .....................................

It is similar to the second visual display in "my traceroute's" (aka mtr)
and provide a way to spot subtle availability changes.


Building
--------

xping hasn't surrendered to autoconf yet, but it should build on Linux,
FreeBSD and OSX. There are a few options in the Makefile that can be
enabled by uncommenting them. OSX users with Terminal.app may wish to
use ncurses.

xping depends on libevent, if you don't have it you can uncomment the
"static linking" option in the Makefile to have it downloaded and linked
static into xping. OSX doesn't use -lrt.

    vi Makefile
    make
    make install

N.B. xping will be installed set-uid because most platforms requires
superuser privileges to open RAW sockets. xping drops the privileges
when it has opened the sockets.


Changes
-------

v1.2

  * unprivileged icmp-unpriv module
  * split out icmp function in seperate module
  * ui improvements (selective updates, disable local-echo)
  * probe count (to limit execution)
  * report generation (when stdout is a file)

v1.1

  * replaced BSD queue.h with utlist.h by Troy D. Hanson
  * improved dns lookup
  * dynamic linking
  * target list from stdin
  * edge detection
  * raw ansi as alternative to ncurses

v1.0

  * hash table lookup
  * ipv6


Authors
-------

xping was written by Martin Topholm.

xping uses libevent2 by Niels Provos and Nick Mathewson, and
uthash and utlist by Troy D. Hanson.
