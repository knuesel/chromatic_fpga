# Chromatic FPGA: small fixes

This is a fork of <https://github.com/ModRetro/chromatic_fpga> with small quality of life improvements.

Currently implemented (build `fix1`):

- Battery indicators

   The AA battery level thresholds are adjusted so that the warning icon starts blinking well before the device shuts down. The screen also goes to low power mode (minimum brightness) a bit earlier.

   The thresholds are tuned for [Eneloop batteries](https://lygte-info.dk/review/batteries2012/Eneloop%20AA%20BK-3MCCE%201900mAh%20(White)%202019%20UK.html) but should also work well for other rechargeables.

   For the corresponding changes in the battery indicator of the settings menu you need to flash the corresponding [MCU firmware](https://github.com/knuesel/chromatic_mcu).

- Brightness setting

  The linear intensity scale is replaced with a non-linear scale to match human perception (see [Stevens's power law](https://en.wikipedia.org/wiki/Stevens%27s_power_law)). The steps now feel regular over the whole range of brightness. In particular this gives more fine grained control at low brightnesses.


## Usage

Install openFPGALoader, get a build from the `builds/` directory and flash it with

```
openFPGALoader --write-flash --cable gwu2x --reset <file>
```

(On Linux, you might need to add a udev rule or run the command as root to make it work.)

See the [original project page](https://github.com/ModRetro/chromatic_fpga) for more information on building and flashing.
