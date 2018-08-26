#Keyboard Layout
The configuration file [`kbfirmware.com.json`](kbfirmware.com.json) can be loaded by any hosted [`QMKBuilder`](https://github.com/ruiqimao/qmkbuilder) instance. Several examples:

* [kbfirmware.com](https://kbfirmware.com)
* [qmkeyboard.cn](https://qmkeyboard.cn)

## Specifics

In order to get backlight control, the top left button was turned into a momentary switch to layer 1. On layer one, the rightmost buttons control the backlight.

## Flashing the Pro Micro

The following instructions apply to Windows machines.
You will need [avrdude](https://sourceforge.net/projects/winavr/) intalled.

0. Compile `kbfirmware.com.json` into a `.hex` file with a QMKBuilder instance.
1. Plug your Pro Micro
1. Open Device Manager
1. Ground the reset pin of the Pro Micro for a few seconds, then let go. You should see a 'Arduino Pro Micro Bootlaoder' device appear. Please note the COM Port number it handles.
1. Ground the reset pin again, the n release, then immediately run the following command:

```bash
$ avrdude -p atmega32u4 -P <YOUR COM PORT NAME HERE> -c avr109 -U flash:w:<YOU HEX FILE HERE> -v
```

So, for example:

```bash
$ avrdude -p atmega32u4 -P COM7 -c avr109 -U flash:w:ottoproto1.hex -v
```

If you did everything well, you should see the Pro Micro get flashed with the configured QMKFirmware.
