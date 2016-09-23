squid-3.5.20 - osx-devpf-transparent patch
==========================================

The /dev/pf device on OSX does not provide the redirection state by ioctl, therefore causing squid to 
get into a redirection loop. OSX gives the ability to retrieve the same information using the pfctl 
command-line. This patch uses the result from pfctl command-line to determine the redirection states. 
This is similiar to mitmproxy.

The patch code is conditionally compiled and is enabled with **_D_SQUID_APPLE**. Compiled with:

```
configure --disable-debug --disable-dependency-tracking --enable-ssl --enable-ssl-crtd --disable-eui --enable-pf-transparent --with-included-ltdl --with-openssl --enable-delay-ools --enable-disk-io=yes --enable-removal-policies=yes --enable-storeio=yes CPPFLAGS="-D_SQUID_APPLE -Wno-error=deprecated-declarations" LDFLAGS=-lresolv
```
