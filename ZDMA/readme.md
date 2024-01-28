LightingZDMA - PCIe to Thunderbolt:
=================
This project contains software and HDL code for the [LightingZDMA board](https://lightingz.store/products/lightingzdma-fastest-dma-thunderbolt-interface-1gb-s-best-dma-ever-the-ultimate-experience).

Once flashed it may be used together with the [PCILeech Direct Memory Access (DMA) Attack Toolkit](https://github.com/ufrisk/pcileech/) or [MemProcFS - The Memory Process File System](https://github.com/ufrisk/MemProcFS/) to perform DMA attacks, dump memory or perform research.

> :warning: **ZDMA have additional requirements**. Make sure the [requirements](#Requirements) are met before purchase.

> :warning: **ZDMA uses a test signed driver** as the driver is not yet signed by Microsoft. The controlling computer must be running in driver testing mode to support ZDMA.

Capabilities:
=================
* Retrieve memory from the target system over Thunderbolt in excess of 800MB/s.
* Access physical memory of target system unless protected with VT-d/IOMMU.
* Raw PCIe Transaction Layer Packet (TLP) access.

For information about more capabilities check out the general readme and info wiki pages at: [PCILeech](https://github.com/ufrisk/pcileech/), [MemProcFS](https://github.com/ufrisk/MemProcFS/) and [LeechCore](https://github.com/ufrisk/LeechCore/) for information about features and capabilities.

For information about other supported FPGA based devices please check out [PCILeech FPGA](https://github.com/ufrisk/pcileech-fpga/).


The Hardware: LightingZDMA
========================
The LightingZDMA PCIe gen2 x4 board contains a powerful Artix7 100T FPGA which allows for good performance and also interesting applications besides PCILeech/MemProcFS. The LightingZDMA may be purchased from: [lightingz.store](https://lightingz.store/products/lightingzdma-fastest-dma-thunderbolt-interface-1gb-s-best-dma-ever-the-ultimate-experience). For more information about the hardware please check out [lightingz.store](https://lightingz.store/products/lightingzdma-fastest-dma-thunderbolt-interface-1gb-s-best-dma-ever-the-ultimate-experience). Please note that the LightingZDMA is sold by a 3rd party and not by the PCILeech project itself!

The picture below depicts an LightingZDMA. The ZDMA contains a Thunderbolt port for data transfer and an update port for easy updating without the need for additional hardware.

<img src="https://gist.githubusercontent.com/ufrisk/c5ba7b360335a13bbac2515e5e7bb9d7/raw/65984ae014a8caa659c2e297dbb77c6c67c0889a/zdma-500.jpg"/>


Requirements:
=================
* A PCIe x4 or PCIe x16 slot on the target computer.
* A Thunderbolt capable port on the controlling computer.
* 64-bit Windows on the controlling computer.

Flashing:
=================
Please note that this instruction applies to the built-in JTAG update port.
1) Install Vivado WebPACK or Lab Edition (only for flashing).
2) Build PCILeech ZDMA (see below) alternatively download and unzip pre-built binary (see below in releases section).
3) Open Vivado.
4) Open Hardware Manager found on the Vivado start screen.
5) Open target. Make sure the USB cable is connected to the JTAG port of the ZDMA device.
6) Flash using Xilinx Vivado Hardware Manager (shown below). Make sure you flash `xc7a100t_0` (the other fpga must not be flashed)! Please select memory part: `is25lp128f`.
7) Finished !!!

<img src="https://gist.githubusercontent.com/ufrisk/c5ba7b360335a13bbac2515e5e7bb9d7/raw/6ad379a64900c8afb74f926445750ddaf3128fa0/zdma-flash.png"/>


Building:
=================
1) Install Xilinx Vivado WebPACK 2023.2 or later.
2) Open Vivado Tcl Shell command prompt.
3) cd into the directory of ZDMA (forward slash instead of backslash in path).
4) Run `source vivado_generate_project.tcl -notrace` to generate required project files.
5) Run `source vivado_build.tcl -notrace` to generate Xilinx proprietary IP cores and build bitstream.
6) Finished !!!

Building the project may take a very long time (~1 hour).

The PCIe device will show as Xilinx Ethernet Adapter with Device ID 0x0666 on the target system by default. For instructions how to change the device id and other advanced build properties check out the [build readme](build.md) for information.


Other Notes:
=================
The completed solution contains Xilinx proprietary IP cores licensed under the Xilinx CORE LICENSE AGREEMENT. This project as-is published on Github contains no Xilinx proprietary IP. Published source code are licensed under the MIT License. The end user that have downloaded the no-charge Vivado WebPACK from Xilinx will have the proper licenses and will be able to re-generate Xilinx proprietary IP cores by running the build detailed above.


Support PCILeech/MemProcFS development:
=======================================
**Thank You LightingZDMA for supporting the PCILeech project :sparkling_heart:**

Some other hardware sellers have chosen not to support the project! If you think PCILeech and/or MemProcFS is awesome or if you had a use for it it's now possible to support the project via Github Sponsors: [`https://github.com/sponsors/ufrisk`](https://github.com/sponsors/ufrisk).

To all my sponsors, Thank You :sparkling_heart:


Releases / Version History:
=================
v4.14
* Initial Release
* Download pre-built binaries below:
  * [ZDMA](https://mega.nz/file/QDphFJBZ#CUhZcoysPE2i2PzZZVp9yvqvWsDFHfcFxylPpsg37cU) SHA256: `5a216a67af01760d67b238a76a1e73b5955c12995d782812004e0d4d02e59d08`
