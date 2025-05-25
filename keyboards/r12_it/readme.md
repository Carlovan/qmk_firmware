# k12 (itlabs version)


![k12](https://imgur.com/a/SCxU86b)


* A custom firmware for Khor R12 keypad by ITLabs *

> see [QMK fork on github](https://github.com/itarozzi/qmk_firmware/tree/itarozzi/keyboards/r12_it)

Based on the original work by [Khor](https://github.com/MoltenKhor/R12) this firmware build is intended to use the keypad as controller for my favorite applications.

The **R12 keypad** consists of:

- a 4x3 Matrix Switch 
- a single Encoder with push switch
- an I²C Oled Display

## Hardware details

The **R12 Keypad** use a **Helios** board based on **RP2040** microcontroller.
 

The 4x3 matrix uses pins described in keyboard.json file.

```
/*
     * Matrix Layout and Pinout
     
            GP22 GP26 GP27 GP28    GP29
           ┌────┬────┬────┬────┬──────────────┐
      GP7  │  0 │  1 │  2 │  3 │ EncoderSwitch│
           ├────┼────┼────┼────┼──────────────┤ 
      GP8  │  4 │  5 │  6 │  7 │    n.c.
           ├────┼────┼────┼────┤
      GP9  │  8 │  9 │ 10 │ 11 │    n.c.
           └────┴────┴────┴────┘
           
*/
``` 

The Encoder switch is connected to GP29 and GP7 pins, so it can be used
in the matrix controller, as regular keyboard switch

The encoder is connected directly to pins GP6 and GP5

The I2C display is connected to SDA/SCL pins (GP6, GP5) 


> I modified original R12 `keyboard.json` file adding encoder switch connections.

> According the new layout definied in `keyboard.json` the keymaps array in the `keymap.c` should be updated, adding a more key.



## Original informations

* Keyboard Maintainer: [Marco Pontone](https://github.com/MoltenKhor)
* Hardware Supported: *Khor R12*
* Hardware Availability: [Khor](https://github.com/MoltenKhor/R12)

Make example for this keyboard (after setting up your build environment):

    make k12:default

Flashing example for this keyboard:

    make k12:default:flash

See the [build environment setup](https://docs.qmk.fm/#/getting_started_build_tools) and the [make instructions](https://docs.qmk.fm/#/getting_started_make_guide) for more information. Brand new to QMK? Start with our [Complete Newbs Guide](https://docs.qmk.fm/#/newbs).

## Bootloader

Enter the bootloader in 3 ways:

* **Bootmagic reset**: Hold down the key at (0,0) in the matrix (usually the top left key or Escape) and plug in the keyboard
* **Physical reset button**: Briefly press the button on the back of the PCB - some may have pads you must short instead
* **Keycode in layout**: Press the key mapped to `QK_BOOT` if it is available
