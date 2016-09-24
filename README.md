squid
=====

Manage custom patches for [squid](http://www.squid-cache.org).

 1. osx-devpf-transparent - OSX support of transparent firewall. With the change to only support /dev/pf style firewalls, and    apple not having public ioctl available on /dev/pf in the same way as OpenBSD. Reverted to use pfctl to get the needed      state information, keeping squid from getting into a forwarding loop. This is the same manner that mitmproxy does.
 
Current options to compile on MacOSX, including the conditional compilation for patch #1 above.

```
./configure --disable-debug --disable-dependency-tracking --enable-ssl \
--enable-ssl-crtd --disable-eui --enable-pf-transparent --with-included-ltdl \
--with-openssl --enable-delay-ools --enable-disk-io=yes \
--enable-removal-policies=yes --enable-storeio=yes \
CPPFLAGS="-D_SQUID_APPLE -Wno-error=deprecated-declarations" \
LDFLAGS=-lresolv
```
