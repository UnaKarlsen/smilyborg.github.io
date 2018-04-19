---
layout: default
title:  "HackRF Firmware update"
date:   2018-04-19 20:00:00 -0200
categories: HackRF SDR firmware software defined radio
---

sudo apt install hackrf gcc-arm-none-eabi cmake dfu-util git

git clone https://github.com/mossmann/hackrf
cd hackrf

git submodule init
git submodule update
cd firmware/libopencm3
make

hackrf_usb
mkdir build
cd build
cmake ..
make

hackrf_spiflash -w hackrf_usb.bin
or
dfu-util --device 1fc9:000c --alt 0 --download hackrf_usb.dfu

