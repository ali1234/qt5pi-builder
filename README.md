Builds Qt 5 and QtQuick for Raspberry Pi.

This is an automated and repeatable version of https://wiki.qt.io/RaspberryPi2EGLFS

Usage:

* Install dependencies:
  - sudo apt-get install multistrap
* Run ./build
* Copy qt5pi directory to /opt/qt5pi on your Pi.
  - You can use the synctopi script for this.
  - You need to create the writable directory manually the first time.

What it does:

* Download ARM toolchain from Linaro.
* Build a Raspbian sysroot using multistrap.
* Download and cross compile qtbase from git.
* Build qtxmlpatterns and qtdeclarative against qtbase.

Hacking:

* If you want to change Qt5 configuration edit ./build.
* If you need extra libs in the sysroot, edit sysroot.config then delete sysroot/ and run ./build.
* If you are going to rebuild this a lot, use apt-cacher-ng to save redownloading packages:
  - sudo apt-get install apt-cacher-ng
  - export http_proxy=http://localhost:3142
  - ./build
