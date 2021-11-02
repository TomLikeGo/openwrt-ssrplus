here is just a set of files for me to log how an openwrt be built together with popular proxies of ssr plus and others. the regular openwrt source be used for this and can download from openwrt.org. 
1. an ubuntu 20.04 is been used for build openwrt and all need depandencies has been installed.
2. whole openwrt source is been cloned
3. v19.01.7 has been checked out and changed the file of feeds.conf.default
4. updated and installed all feeds, the comunite packages, and choose modules what u need as following
  ./scripts/feeds update -a && ./scripts/feeds install -a
  make menuconfig
5. just start to build 
   make -j8
  got a error that golang doesn't works to build v2ray which coded by go. 
6.here is a way to solve the issue. u just need to use a newer version of go. the go v1.16.9 has been used and u may used another one. update the file 
  feeds/packages/lang/golang/golang-version.mk
  just put a version number in it. and another Makefile need to be update with new hash number
  feeds/packages/lang/golang/golang/Makefile
  buid again
7.if an error found with upx not found, just simply copy your upx in /usr/bin to the dir then run make agian.



<!---
TomLikeGo/TomLikeGo is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
