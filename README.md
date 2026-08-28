# ti-ot-rcp-cc2652p

CI that builds a custom **OpenThread RCP** firmware from
[`TexasInstruments/ot-ti`](https://github.com/TexasInstruments/ot-ti) for a
button-less CH340-based **CC2652P** Zigbee/Thread USB dongle.

Customization vs. stock `ot-rcp`:

- **UART 460800 baud** (stock is 921600 — marginal on a CH340). No hardware flow
  control (already the driver default; the dongle has no RTS/CTS anyway).
- Built for `CC1352P_2_LAUNCHXL` (`cc13x2_cc26x2`, UART on DIO12/DIO13).

Run the **build-ot-rcp** workflow, then download the `ot-rcp.hex` artifact and
flash it with `flash_dongle.py --file ot-rcp.hex`.

Use as the radio for a Home Assistant **OpenThread Border Router** add-on
(`/dev/ttyUSB0`, 460800) + **Matter Server** add-on.
