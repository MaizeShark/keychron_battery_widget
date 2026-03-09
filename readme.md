# Keychron Battery Widget

A small widget to display the battery state of the Keychron M5 in wireless 2.4GHz mode.

currently supported devices:
- Keychron M5 (3434:d028)

> Should work on any desktop which supports system tray.

Provided by default for Linux via AppImage, should work on Windows but will require manual compilation to an exe.

---------------------
If you'd like for your Keychron Mouse/Keyboard to be supported, open an issue following the instructions below:

1. Run ``lsusb``, find your device and copy its ID, also note the bus number and device number
2. Install Wireshark
3. Run ``sudo modprobe usbmon`` and then run ``sudo -E wireshark`` in elevated privilages via sudo
4. Start monitoring the interface matching your device's bus number in Wireshark (e.g. bus 1 → ``usbmon0`` / ``usb0``, bus 2 → ``usbmon1`` / ``usb1``). To actually see what's going on, use the filter ``usb.dst ~ "<bus number>.<device number>"`` or ``usb.src ~ "<bus number>.<device number>"``, replacing the numbers with the outputs from lsusb.
5. Open the Keychron App, find an event in Wireshark that has "report" in the event name, screenshot it and copy its byte representation.
6. Open Keychron App once more with a different battery level.
7. Run ``sudo modprobe -r usbmon`` to disable USB monitoring
