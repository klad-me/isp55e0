ISP-55e0 - An ISP flashing tool for the WCH CH579

This tool is meant to flash a WinChipHead CH579 through USB on
Linux.

A few similar tools exist for other WCH chips (namely for the CH55x
series like the CH554) but all appear unmaintained and / or are
without a proper license:

  * https://github.com/rgwan/librech551
  * https://github.com/NgoHungCuong/vnproch551
  * https://github.com/LoveMHz/vnproch55x   (descendant of vnproch551)

So the wheel has to be re-invented.

When set in ISP mode, the chip creates a 4348:55e0 USB device, hence
the name for that project. The bootloader that comes the CH579 is
version 2.8.0, and that's the only one supported for now.

A drawback of these devices is that the firmware has to be sent
encrypted to the device. This is just annoying. The encrypting
algorithm is not known to me, but it is rather weak since it's
vulnerable to a replay attacks. However it's likely the encryption key
is tied to a device through its unique ID, as it is the case for the
previous bootloaders. There are plenty of other manufacturers who
don't do that stupid shit.

Usage
-----

Query the device:

  ./isp55e0

Flash some firmware:

  ./isp55e0 -f fw.bin