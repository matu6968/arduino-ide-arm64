# Arduino IDE 2.x for ARM64
This repo contains Arduino IDE version 2.x compiled for ARM64 devices (such as for Raspberry Pi devices)
Build requirements:
- any ARM64 device with atleast 8 GB of RAM + 3 GB swap if running a heavier distro or with apps open
- build dependencies listed on the [git repo](https://github.com/arduino/arduino-ide/blob/main/docs/development.md#Prerequisites)

Build instructions:
1. Clone [Arduino IDE](https://github.com/arduino/arduino-ide) source (make sure you have enough space)
2. replace package.json inside of electron-app folder to the one located in this repo
3. Make sure any electron-builder prebuilt packages are ARM64 compatible (like fpm, install using gem install fpm then copy the dir to the electron-builder directory) so that the build does not fail with a incompatible binary error
4. build using the usual commands listed in build guide in ["Run From Source"](https://github.com/arduino/arduino-ide/blob/main/docs/development.md#run-from-source) and package it in section ["Bundle the Application"](https://github.com/arduino/arduino-ide/blob/main/docs/development.md#bundle-the-application)
