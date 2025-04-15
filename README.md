# Arduino IDE 2.x for ARM64

This repo contains Arduino IDE version 2.x binaries compiled for ARM64 devices (such as for Raspberry Pi devices)

## ⚠️ This is not a fork of Arduino IDE, this is only instructions to build the IDE for ARM64 platforms ⚠️ 

Build requirements:
- any ARM64 device running Debian, Raspberry Pi OS or Ubuntu (ideally the newest versions) with atleast 8 GB of RAM + 3 GB swap due to webpack eating ram
- build dependencies listed on the [git repo](https://github.com/arduino/arduino-ide/blob/main/docs/development.md#Prerequisites)
- golang 1.21 or newer (needed to compile arduino-language-server and arduino-cli, install instructions: https://go.dev/doc/install)

Build instructions:
1. Clone [Arduino IDE](https://github.com/arduino/arduino-ide) source (make sure you have enough space)
2. `git apply` the `add-home-page-email-deb.diff` file to `electron-app/package.json`
This updates the required fields to make a .deb package and updates certain dependencies (like Electron)
3. Make sure any electron-builder prebuilt packages are ARM64 compatible 
Typically fpm in electron-builder *is only suited for x86*, so to solve the issue to prevent further errors:
- install fpm via gem: `fpm install fpm`
- copy over the fpm script to the ~/.cache/electron-builder/fpm/fpm-1.9.3-2.3.1-linux-x86 (or similar) directory:
```
rm ~/.cache/electron-builder/fpm/fpm-1.9.3-2.3.1-linux-x86/fpm
cp /usr/local/bin/fpm ~/.cache/electron-builder/fpm/fpm-1.9.3-2.3.1-linux-x86/fpm
```
4. Build using the usual commands listed in build guide in ["Build From Source"](https://github.com/arduino/arduino-ide/blob/main/docs/development.md#build-from-source), if it failed building with SIGKILL error, increase swap/close programs (alternatively you can use this script at https://github.com/Botspot/pi-apps/issues/2585#issuecomment-2477847933 to automatically install dependencies and build the package)
5. To build a DEB package after you patched electron-app/package.json with additional required fields, use the listed commands in section ["Bundle the Application"](https://github.com/arduino/arduino-ide/blob/main/docs/development.md#bundle-the-application) (yarn --cwd electron-app package)
[FAQ](https://github.com/matu6968/arduino-ide-arm64/wiki/faq)
