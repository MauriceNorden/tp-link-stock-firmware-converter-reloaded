# tp-link-stock-firmware-converter RRELOADED
I've created this fork because of problems creating a stock firmware image for my `TL-WPA8631P`
The origional repo and tool used an older version of the `tplink-safeloader` binary.
After some digging i tracked down a more recent version with compatibility for the my device [link](https://lxr.openwrt.org/source/firmware-utils/src/tplink-safeloader.c) (and many more, will try adding compatibility list later).

I've added the used files in the `src` folder, they are not compiled but you can with the instructions (See section `How to build`)

The `safeloader.html` is still the origional from Github user [`argsnd`](https://github.com/argsnd)
Exept for the hyperlinks.


# How to build
1. Install [Emscripten](https://emscripten.org/docs/getting_started/downloads.html).
2. clone repo and enter the `src` folder 
3. Compile tplink-safeloader: 
```bash
emcc tplink-safeloader.c md5.c -o safeloader.js -s FORCE_FILESYSTEM=1 -s EXIT_RUNTIME=1 -s EXPORTED_RUNTIME_METHODS=FS
```
4. Run safeloader.html from a web server such as `python3 -m http.server` as most browsers don't support file:// XHR requests.

# How to use the prebuild binaries

1. enter folder `bin`
2. Run safeloader.html from a web server such as `python3 -m http.server` as most browsers don't support file:// XHR requests.
2. navigate to the webservers url [`http://localhost:8000`](https://localhost:8000)
3. upload your firmware and place `sysupgrade.bin` onto a TFTP server

# [Link to the new version of the tool](https://cdn.mndevs.host/tplink-safeloader/)

