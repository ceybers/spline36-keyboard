# Firmware

## QMK and Vial
For the firmware, I used QMK. Once the QMK firmware is working OK, I then port my config to Vial and compile a QMK/Vial firmware.

For some reason I had a lot of issues this time. Despite things being almost identical to my previous split keyboard build, I couldn't get the keyboard halves to work together.

It took more time than I'd like to admit, but eventually I got it to work. In the end, I used the pin method to determine handedness, where you wire a pin to HIGH (3v3) on one of the halves to identify it as the master board, and the second half will without this pin wired HIGH will then default to slave.

Some advice is to use a multimeter to make sure the slave board is receiving power from the master board across whichever split link you use. If your MCU has an onboard LED, configure your firmware to turn it on at boot. This will let you easily notice if wires come loose while testing. 

If you haven't used Boot Magic before, set it up. This allows you to hold a key (e.g., top-left key) while plugging the keyboard in to boot into bootloader mode. This is usually much more convenient than trying to hold the BOOTSEL button on a MCU. And if you don't have one, consider a small USB2 hub that has on/off buttons for each port, which is much more convenient than physically removing and reinserting plugs.

Lastly, ensure the pin you are using is compatible with your protocol method (e.g., USART TX). On newer boards like the RP2040 this is not as much of a restriction, but while testing you want to remove as many variables as possible.

## Notes
- For my base layout, I use [Colemak-DH](https://colemakmods.github.io/mod-dh/).
- For split keyboards in particular, I like to start with Manna Harbour's [Miryoku layout](https://github.com/manna-harbour/miryoku).
- If you opt to use Home Row Mods (and you should definitely give them a try, at least once), then [precondition's definitive article on Home Row Mods](https://precondition.github.io/home-row-mods) is a must read.
- If you end up accidentally triggering unwanted modifiers on the same hand, have a look at Manna Harbour's [Bilateral Combinations](https://github.com/manna-harbour/qmk_firmware/blob/bilateral-combinations/docs/tap_hold.md#bilateral-combinations).
- The next thing I'd suggest having a look at is Pascal Getreuer's Achordion library: [Achordion: Customizing the tap-hold decision](https://getreuer.info/posts/keyboards/achordion/index.html).
---

⏪ [Construction](Construction.md) | ⏯️ *Firmware* | ⏩ [Gallery](Gallery.md) | ⏏️ [README.md](../README.md)