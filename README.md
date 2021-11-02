here is just a set of files for me to log how an openwrt be built together with popular proxies of ssr plus and others. a regular openwrt source has been used for this and it could be downloaded from openwrt.org. 
1.an ubuntu 20.04 is been used for build openwrt and all need depandencies has been installed.
2.whole openwrt source is been cloned
3.v19.01.7 has been checked out and changed the file of feeds.conf.default. add following lines to end of the file.
  src-git lienol https://github.com/Lienol/openwrt-package.git;main
  src-git kenzo https://github.com/kenzok8/openwrt-packages
  src-git small https://github.com/kenzok8/small

5.update and install all feeds, all comunite packages, and choose modules what u need. commands here as following
   ./scripts/feeds update -a && ./scripts/feeds install -a
   make menuconfig
6.then just start to build 
   make -j8
  if got a error that golang doesn't works to build v2ray-core or xray, that because they are coded by go. 
7.here is a way to solve the issue. u just need to switch to a newer version of go. go v1.16.9 is which I used and u may used another one. u have to update the files 
  feeds/packages/lang/golang/golang-version.mk
  just put a version number in it. and another Makefile need to be update with new hash number
  feeds/packages/lang/golang/golang/Makefile
  buid again
8.if an error pops up with upx not found, just simply copy your upx in /usr/bin to the dir then run the make agian.
it should be work!

thank Lieno, https://github.com/Lienol/openwrt gives me hints to try this.

<!---
TomLikeGo/TomLikeGo is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
