# Arduino IDE 2.x for ARM64
This repo contains Arduino IDE version 2.x compiled for ARM64 devices (such as for Raspberry Pi devices)
Build requirements:
- any ARM64 device running Debian or Raspberry Pi OS (cannot be Ubuntu due to compiling issues) with atleast 8 GB of RAM + 3 GB swap
- build dependencies listed on the [git repo](https://github.com/arduino/arduino-ide/blob/main/docs/development.md#Prerequisites)
- golang 1.21 or newer (install instructions: https://go.dev/doc/install)

Build instructions:
1. Clone [Arduino IDE](https://github.com/arduino/arduino-ide) source (make sure you have enough space)
2. replace package.json inside of electron-app folder to the one located in this repo
3. Make sure any electron-builder prebuilt packages are ARM64 compatible (like fpm, install using gem install fpm then search for fpm in root dir and copy the dir of found fpm dir that you installed to the electron-builder directory) so that the build does not fail with a incompatible binary error
4. build using the usual commands listed in build guide in ["Build From Source"](https://github.com/arduino/arduino-ide/blob/main/docs/development.md#build-from-source), if it failed building with SIGKILL error, increase swap (alternatively you can use this script at https://github.com/Botspot/pi-apps/issues/2585#issuecomment-2477847933 to automatically install depnendencies and build the package)
5. To build a DEB package, if you replaced package.json then use the listed commands in section ["Bundle the Application"](https://github.com/arduino/arduino-ide/blob/main/docs/development.md#bundle-the-application) (yarn --cwd electron-app package)
[FAQ](https://github.com/matu6968/arduino-ide-arm64/wiki/faq)
