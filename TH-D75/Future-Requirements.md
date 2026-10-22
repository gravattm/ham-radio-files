# Future Requirements — TH-D75 channel file

Planned additions and open questions for `Tucson-Area_TH-D75.THD75`.

## Planned channels

### FRS / GMRS (receive only)

Add the 22 FRS/GMRS channels as receive-only memories. The D75 receives 410–470 MHz on both bands, but it can't legally transmit there: it isn't Part 95 certified, and GMRS needs its own FCC license.

| Channels | Frequencies (MHz) |
|---|---|
| 1–7 | 462.5625 – 462.7125, every 25 kHz |
| 8–14 | 467.5625 – 467.7125, every 25 kHz |
| 15–22 | 462.5500 – 462.7250, every 25 kHz |

**Blocker:** channels 1–14 sit on 12.5 kHz offsets (e.g. 462.5625), which the 5 kHz step can't land on. The radio's fine-step setting has to be decoded first: set Fine Step on one channel in the Kenwood software, save, and compare with the previous file.

### Other services to consider (receive only)

- **MURS:** 151.820, 151.880, 151.940, 154.570, 154.600 MHz.
- **Marine VHF:** 156–162 MHz, e.g. channel 16 (156.800).
- **CB:** 26.965–27.405 MHz in AM on band B. The stock antenna performs poorly at these frequencies.

## Open questions

- **KHYT 107.5 (065):** sources disagree on whether K-Hit is still on 107.5. Remove the channel if it's silent.
- **TUS ground control:** not added because sources disagree (124.4 vs 120.025). Confirm against a current FAA chart.
- **LEMN DSU (025):** no D-STAR routing callsigns set yet (003 uses `CQCQCQ` via `K7TUS  B` / `K7TUS  G`).

## File format still to decode

Each of these needs one setting changed in the Kenwood software and a save, so the files can be compared (see the record layout in `CLAUDE.md`):

- Lockout
- DCS code (023 is the default and changes no byte, so a different code is needed)
- Fine step
