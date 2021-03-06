---
layout: page
title: "Raspberry Pi RF Switch"
description: "Instructions how to integrate devices controlled via codes sent with low-cost GPIO RF modules on a Raspberry Pi into Home Assistant as a switch."
date: 2016-05-10 09:00
sidebar: true
comments: false
sharing: true
footer: true
logo: raspberry-pi.png
ha_category: Switch
ha_release: 0.19
---


The `rpi_rf` switch platform allows you to control devices over 433/315MHz LPD/SRD signals with generic low-cost GPIO RF modules on a [Raspberry Pi](https://www.raspberrypi.org/).

Interoperable with codes sniffed via [the rpi-rf module](https://pypi.python.org/pypi/rpi-rf) or [rc-switch](https://github.com/sui77/rc-switch).
For more info see the PyPi module description: [rpi-rf](https://pypi.python.org/pypi/rpi-rf).

To enable, add the following to your `configuration.yaml`:

```yaml
# Example configuration.yaml entry
switch:
  platform: rpi_rf
  gpio: 17
  switches:
    bedroom_light:
      code_on: 1234567
      code_off: 1234568
    ambilight:
      pulselength: 200
      code_on: 987654
      code_off: 133742
    living_room_light:
      protocol: 5
      code_on: 654321
      code_off: 654320
```

Configuration variables:

- **gpio** (*Required*): GPIO to which the data line of the TX module is connected.
- **switches:** (*Required*): The array that contains all switches.
  - **[entry]** (*Required*): Name of the switch. Multiple entries are possible.
    - **code_on** (*Required*): Decimal code to switch the device on.
    - **code_off** (*Required*): Decimal code to switch the device off.
    - **protocol** (*Optional*): RF Protocol (Default is `1`).
    - **pulselength** (*Optional*): Pulselength (Default is the protocol default).

