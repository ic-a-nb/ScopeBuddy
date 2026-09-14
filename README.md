# ScopeBuddy Fork, changes for the 9" Version V1.0

This project is an adapted version of [ScopeBuddy](original-repository-link), licensed under the [ScopeBuddy Community License 1.0](license-link).

## What you need

| Component | Requirement | References and sources |
| --- | --- | --- |
| Display | Elecrow CrowPanel Advanced 9-inch, ESP32-P4, 1024 × 600 (`DHE04209D`) | [Official product page][crowpanel-product] · [Elecrow documentation][crowpanel-wiki] · [Github][crowpanel-github] |
| Oscilloscope | One channel for the basic lessons; two channels for all lessons | Use high-impedance inputs and probes suitable for 3.3 V logic |
| USB cable | USB data cable for installing the firmware | Charge-only cables do not work |
| Rotary encoder (optional) | GIAK KY-040 module or a compatible 3.3 V encoder module | [Wiring guide](ENCODER.md) · [Amazon.de][encoder-amazon] |
| Enclosure (optional) | The enclosure needs to be stretched to fit the 9-inch version. |

The Amazon links are non-affiliate purchase links. Listings and availability can
change; use the model names and electrical requirements above when selecting an
equivalent component.

## Assemble the hardware

1. Disconnect USB and any other power source before wiring the optional rotary
   encoder.
2. Connect the encoder as described in the [wiring guide](ENCODER.md). Power it
   from 3.3 V, not 5 V.
3. Connect oscilloscope CH1 to `GPIO49`. For two-channel lessons, connect CH2 to
   `GPIO47`. Connect both probe grounds to board `GND`.

GPIO49 and GPIO50 are 3.3 V logic outputs intended only for high-impedance
oscilloscope or logic-analyzer inputs. Do not connect loads or external voltages
to these pins. The pins also share expansion connector functions; do not attach
an expansion UART or SPI device while ScopeBuddy is generating signals.

## Build from source
ScopeBuddy 0.5.1 is built and hardware-tested with ESP-IDF 5.4.2. Install and
activate ESP-IDF, then run:

```sh
idf.py set-target esp32p4
idf.py build
idf.py flash monitor
```

ESP-IDF's component manager downloads the required LVGL, display, and touch
components. `dependencies.lock` pins the component versions used for release
builds.

## License
This project is a modified version of ScopeBuddy and is subject to the same license terms.

Original ScopeBuddy contributions are available under the
[ScopeBuddy Community License 1.0](LICENSE.md). You may build, study, modify,
and publish them, including for education and research. Published modified
versions must provide their corresponding source, retain a reference to this
project, and use a distinct name.

ScopeBuddy devices and kits may be passed on at direct cost. Selling
them for profit requires a separate commercial license from the repository
owner. ScopeBuddy is therefore source-available, not Open Source as defined by
the Open Source Initiative.

Elecrow-derived board-support material and other third-party components are
not relicensed by ScopeBuddy. Their status and the exact repository license
boundaries are documented in [LICENSE.md](LICENSE.md) and
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

Contributions are welcome under the process in
[CONTRIBUTING.md](CONTRIBUTING.md). Pull requests must accept the
[Contributor License Agreement](CLA.md), which lets contributors retain their
copyright while allowing ScopeBuddy to continue offering separate commercial
licenses.

## Further documentation

- [Rotary encoder wiring](ENCODER.md)
- [Enclosure model and dimensions](hardware/enclosure/README.md)
- [Hardware diagnostics and validation](docs/HARDWARE_VALIDATION.md)
- [Maintainer and release guide](docs/MAINTAINING.md)

[crowpanel-product]: https://www.elecrow.com/crowpanel-advanced-9inch-esp32-p4-hmi-ai-display-1024x600-ips-touch-screen-wifi-6-support.html
[crowpanel-wiki]: https://www.elecrow.com/wiki/CrowPanel_Advanced_9inch_ESP32-P4_HMI_AI_Display_1024x600_IPS.html
[crowpanel-github]: https://github.com/Elecrow-RD/CrowPanel-Advanced-9inch-ESP32-P4-HMI-AI-Display-1024x600-IPS-Touch-Screen
[encoder-amazon]: https://amzn.eu/d/03NJfjfa
[original-repository-link] https://github.com/johannesboernsen/ScopeBuddy
