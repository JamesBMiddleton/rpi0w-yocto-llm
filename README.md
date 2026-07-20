# rpi0w-yocto-llm

A yocto build for running the SmolLM2-135M language model locally on a Raspberry Pi 0 W with the llama.cpp LLM inference engine.

## Build the image
```bash
git clone git@github.com:JamesBMiddleton/rpi0w-yocto-llm.git
cd rpi0w-yocto-llm
git submodule init
git submodule update
export TEMPLATECONF="$PWD/templates/templates/default"
cd poky
source oe-init-build-env
bitbake core-image-base
```

## Flash the image to an SD card
```
export DEVICE="/dev/mmcblk0"
bzcat tmp/deploy/images/raspberrypi0-wifi/core-image-base-raspberrypi0-wifi.rootfs.wic.bz2 | sudo dd of=$DEVICE bs=4m conv=fsync status=progress && sync
```
