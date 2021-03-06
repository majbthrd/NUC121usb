sample Nuvoton NUC121/NUC125 USB device code
============================================

The [Nuvoton NUC121 and NUC125](http://www.nuvoton.com/hq/products/microcontrollers/arm-cortex-m0-mcus/nuc121-125-series/) are Cortex-M0 based USB microcontrollers capable of crystal-less USB operation.  They could be compared to the Atmel/Microchip SAMD11, but have more memory than that device.

At present, source code is provided for these sample devices:

* USB CDC to UART bridge
* USB HID mouse emulator

To their credit, Nuvoton already does provide sample code in their [NUC121_Series_BSP_CMSIS](https://www.nuvoton.com/hq/products/microcontrollers/arm-cortex-m0-mcus/nuc121-125-series/Software/?__locale=en&resourcePage=Y) download.  However, that code is focused on the IAR and Keil toolchains.

This code, in contrast, is written for gcc and clang.

It uses a new USB device stack written specifically for the NUC121/NUC125 and uses an API modeled on [vcp](https://github.com/ataradov/vcp).  vcp was written for the SAMD11 / SAMD21.  Since the USB stack APIs are nearly the same, code can be more easily ported between the ataradov vcp USB stack and this NUC121usb one (as well as [NUC126usb](https://github.com/majbthrd/NUC126usb/)).  Another advantage of this approach is that the code size is a little more efficient than the Nuvoton reference code.

## Alternatives

I've also contributed a NUC121/NUC125/NUC126 driver to [TinyUSB](https://github.com/hathach/tinyusb).  Since TinyUSB runs on many different microcontrollers, code originally written for one device can often be readily adapted to many others.

## Build Requirements

One approach is to use [Rowley Crossworks for ARM](http://www.rowley.co.uk/arm/) to compile this code.  It is not free software, but has been my favorite go-to ARM development tool for a decade and counting.  Rowley does not officially support the Nuvoton NUC121/NUC125, but you can [download an open-source CPU support package for the NUC121/NUC125](https://github.com/majbthrd/MCUmisfits/).

*OR*

I've modified the build environment provided by [mcu-starter-projects](https://github.com/ataradov/mcu-starter-projects) to work with the NUC121.  With this approach, the code can be built using only open-source software.  In Ubuntu-derived distributions, this is likely achieved with as little as:

```
sudo apt-get install gcc-arm-none-eabi libnewlib-arm-none-eabi build-essential
```
