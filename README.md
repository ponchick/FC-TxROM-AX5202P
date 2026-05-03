# FC-TxROM-AX5202P

Cartridge PCB with an MMC3 mapper built around the AX5202P IC.

In theory, such a cartridge should support all TxROM-family board types. In practice, only the most common variants have been tested — no issues were found.

Russian version: [`README.ru.md`](README.ru.md)

## PRG RAM and battery support

The board supports PRG RAM for save data. A CR2032 cell retains data when the console is powered off.

- **If a battery is installed** (saves are required) — leave the **NO BATTERY** jumpers **open** (do not bridge them).
- **If no battery is used** (PRG RAM is on the board but saves are not needed) — bridge **both** **NO BATTERY** jumpers. PRG RAM is then powered from the console’s main supply, and data is lost when power is removed.

In no-battery mode, the following parts may be omitted:

- Battery BT1
- Resistors R1, R2, R4
- Capacitors C4, C8
- Diodes D1, D2
- Transistor Q1

## CHR ROM / CHR RAM selection

Some games need RAM instead of ROM for pattern tables. Selection is done with three jumpers on the board:

- **CHR ROM mode** — bridge the upper pair of pads.
- **CHR RAM mode** — bridge the lower pair of pads.

## Mirror Control (mapper 118 support)

The two **MIRROR CONTROL** jumpers route `CHR A17` and `CIRAM A10`. This is required for correct operation of different TxROM board subtypes.

- **Upper position** — for mapper 118 (**TKSROM** and **TLSROM** boards).
- **Lower position** — for standard TxROM (e.g. **TKROM**, **TLROM**) and most other MMC3 games.

If you do not use mapper 118, keep the jumpers in the lower position.

## ROM type selection (pinout)

Two jumpers switch pins 1 and 31 of the ROM IC, because those pins differ between memory types.

- **Upper position** (`EEPROM/FLASH`) — for electrically erasable ROM (EEPROM) and FLASH.
- **Lower position** (`UV EPROM`) — for UV-erasable EPROM.

Set the jumpers to match the ROM you install.

## License

This project is licensed under **CERN Open Hardware Licence Version 2 – Permissive** (`CERN-OHL-P-2.0`).  
See `LICENSE` for details.

SPDX-License-Identifier: `CERN-OHL-P-2.0`
