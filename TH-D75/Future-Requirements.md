# Future Requirements — TH-D75 channel file

Planned additions and open questions for `Tucson-Area_TH-D75.THD75`.

## Planned channels

### Channels blocked on fine step (receive only)

These sit on 12.5 kHz or 2.5 kHz offsets, which the 5 kHz step can't land on. The radio's fine-step setting has to be decoded first: set Fine Step on one channel in the Kenwood software, save, and compare with the previous file. FRS/GMRS 15–22 are already in (067–074).

| Channels | Frequencies (MHz) |
|---|---|
| FRS/GMRS 1–7 | 462.5625 – 462.7125, every 25 kHz |
| FRS 8–14 | 467.5625 – 467.7125, every 25 kHz |
| VCALL10 (national VHF interop calling) | 155.7525 |
| VTAC11–14 (national VHF interop tactical) | 151.1375, 154.4525, 158.7375, 159.4725 |
| UCALL40 (national UHF interop calling) | 453.2125 |
| UTAC41–43 (national UHF interop tactical) | 453.4625, 453.7125, 453.8625 |

### Other services to consider (receive only)

- **SO-50 satellite:** uplink 145.850 (67.0 Hz tone; 74.4 Hz arms it), downlink 436.795, which drifts ±10 kHz with Doppler. Needs a cross-band split memory, whose encoding isn't decoded yet; compare files after setting one in the Kenwood software.
- **Coronado National Forest / Tucson Interagency Dispatch:** the only sources found were forum posts and a 2019 incident plan (e.g. 172.275, 171.6375, 168.150). Confirm against the current Southwest Area communications guide before adding.
- **Arizona state interoperability:** frequencies not confirmed; check before adding.
- **CB:** 26.965–27.405 MHz in AM on band B. The stock antenna performs poorly at these frequencies.

## Open questions

- **KHYT 107.5 (065):** sources disagree on whether K-Hit is still on 107.5. Remove the channel if it's silent.
- **ZAB TUS (107):** 125.4 comes from an undated LiveATC listing. Confirm it.
- **DM ATIS (086):** 270.1 MHz comes from a single source. Confirm it against the current Chart Supplement.
- **LEMN DSU (025):** no D-STAR routing callsigns set yet (003 uses `CQCQCQ` via `K7TUS  B` / `K7TUS  G`).

## File format still to decode

Each of these needs one setting changed in the Kenwood software and a save, so the files can be compared (see the record layout in `CLAUDE.md`):

- DCS code (023 is the default and changes no byte, so a different code is needed)
- Fine step
