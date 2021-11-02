Here is just a set of files for me to log how an openwrt be built together with popular proxies of ssr plus and others. A regular openwrt source has been used for this and it could be downloaded from openwrt.org. 

1. Ubuntu 20.04 is used for building openwrt and all need depandencies has been installed.

2. Whole openwrt source is been cloned

3. v19.01.7 is checked out and the file of feeds.conf.default is changed in curent dir. Added following lines to end of the file.
```
  src-git lienol https://github.com/Lienol/openwrt-package.git;main
  src-git kenzo https://github.com/kenzok8/openwrt-packages
  src-git small https://github.com/kenzok8/small
```
5. Update and install all feeds, all comunite packages, and choose modules what u need. commands as following
   ```
   ./scripts/feeds update -a && ./scripts/feeds install -a
   make menuconfig
   ```
6. then just start to build 
   ```
   make -j8
   ```
7. if got a error that golang doesn't works to build v2ray-core or xray, and got the message.
  
   build github.com/v2fly/v2ray-core/v4/main: cannot load io/fs: malformed module path "io/fs": missing dot in first path element

   Here is a way to solve the issue. Just switch to a newer version of go. go v1.16.9 is which I used. You have to update the files 
   
   ``` 
   feeds/packages/lang/golang/golang-version.mk
   ```
  just put a version number in it. and another Makefile need to be update with new hash number
  ```
  feeds/packages/lang/golang/golang/Makefile
  ```
  buid it again

8.if an error pops up said upx not found, just simply copy your upx in /usr/bin to the dir then rerun the make.
it should be work!

thank Lieno, https://github.com/Lienol/openwrt gives me hints to try this.

<!---
TomLikeGo/TomLikeGo is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
