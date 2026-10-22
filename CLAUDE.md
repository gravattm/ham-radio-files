# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A data repository of amateur radio programming files, not a software project — there is no build, lint, or test tooling. Files are organized by radio model (currently only `TH-D75/`, for the Kenwood TH-D75 handheld).

## TH-D75 files

- `Tucson-Area_TH-D75.THD75` — **the official file to load onto the radio.** It's a binary memory image for Kenwood's TH-D75 programming software, with 66 channels: 38 repeaters on 2m, 220, 440 and 6m (000–037), then simplex/APRS/ISS, NOAA weather, Tucson aviation (AM) and WWV (AM) (038–055), and Tucson FM broadcast stations in WFM (056–065). The repeaters' tones, modes and frequencies were checked against the Radio Society of Tucson repeater chart (Repeaters page on the RST website) on 2026-10-21. It has no version number on purpose: edit this file in place and let git keep the history. It is binary, so editing it as text corrupts it; see the record layout below.
- `Tucson-Area-Repeaters.md` — a readable table of every channel, with repeaters grouped by band and the other channels by type, plus notes. It's generated from the `.THD75`, so whenever the `.THD75` changes, regenerate it to match: read each used channel's fields using the layout below.
- `THD75_macos.zip` — the vendor's macOS installer (`THD75_macos.dmg`, ~96 MB). Leave it alone.

## Channel conventions

- Names are uppercase and at most 9 characters (the longest in the current file). The software shows longer names truncated.
- Comments start with the repeater's callsign, followed by its location or notes.
- No channel is locked out. "likely out of range" in a comment marks a candidate for lockout, which is set in the Kenwood software.

## `.THD75` record layout

This layout was worked out from the `.THD75` files, checked against the repeater chart, and confirmed by opening edited files in the Kenwood software. Kenwood doesn't document it. All integers are little-endian. Edit the file only by overwriting bytes in place (e.g. a Python script using `struct`); never insert or remove bytes. Keep a backup, and after an edit, re-read every used channel to check nothing else moved.

- **Header:** starts with ASCII `^Kenwood TH-D75`. The u32 at `0x30` is the channel table offset (`0x5E`), and the u32 at `0x34` is the channel count (1000).
- **Channel table:** channel N (0-based) is at `0x5E + N * 0x127`. Each record is 295 bytes, and empty slots are all zero.

| Offset | Size | Field |
|---|---|---|
| `0x00` | u8 | In-use flag (`1` = programmed) |
| `0x01` | u32 | RX frequency, Hz |
| `0x05` | u32 | TX frequency, Hz |
| `0x09` | u32 | Offset, Hz |
| `0x0D` | u8 | Shift: `0` = simplex, `1` = Minus, `2` = Plus |
| `0x0E` | u8 | Operating mode: `0x00` = FM, `0x01` = AM, `0x02` = WFM (broadcast), `0x1B` = DV (D-STAR) |
| `0x0F` | 30 B | Name, UTF-16LE, NUL-padded (names of up to 9 characters appear in the file) |
| `0x2D` | u8 | Tone mode: `0` = None, `1` = Tone, `3` = DCS (`2` is probably CTCSS, unconfirmed) |
| `0x2E` | u8 | TX CTCSS tone index |
| `0x2F` | u8 | RX CTCSS tone index |
| `0x35` | u8 | Always `2` (unknown) |
| `0x3E`, `0x42`–`0x45` | | Always `0xFF` (unknown) |
| `0x85` | 162 B | Comment, UTF-16LE, NUL-padded to the end of the record |

- **CTCSS index:** a position in the standard 50-tone list (67.0 = 0, 69.3, 71.9, 74.4, 77.0, 79.7, 82.5, 85.4, 88.5, 91.5, 94.8, 97.4, 100.0, 103.5, 107.2, 110.9, 114.8, 118.8, 123.0, 127.3, 131.8, 136.5, 141.3, 146.2, 151.4, 156.7, 159.8, 162.2, 165.5, 167.9, 171.3, 173.8, 177.3, 179.9, …). Confirmed in the Kenwood software: 8 = 88.5, 12 = 100.0, 14 = 107.2, 15 = 110.9, 19 = 127.3, 20 = 131.8, 21 = 136.5, 22 = 141.3, 25 = 156.7, 29 = 167.9. So 179.9 is 33. Don't use Kenwood's older 42-tone list, which puts 179.9 at 29. Channels with no tone still store index 8 (the 88.5 default).
- **No checksum:** on 2026-10-21, a copy with a channel's comment changed byte-for-byte opened in the Kenwood software and showed the change.
- **D-STAR callsigns:** these live in a separate table. Each entry is `0x2E` bytes, and channel N's starts at `0x50B75 + N * 0x2E`. It holds URCALL (8 bytes ASCII, e.g. `CQCQCQ`), then a NUL, RPT1 at +9, a NUL, and RPT2 at +0x12. RPT1 and RPT2 are space-padded, for example `K7TUS  B`.
- **Save timestamp:** the Kenwood software writes the save time at `0x509EC` (hour, 12-hour clock) and `0x509ED` (minute). These bytes change on every save, so ignore them when comparing files.
- **Not located yet:** lockout and the DCS code. Setting DCS 023 changed no other byte, so 023 is probably the code table's zero/default value; a non-023 code is needed to find the field. To find one, set it on a single channel in the Kenwood software, save the file under a new name, and compare it with the previous file. Don't try to change these by editing bytes. Make those changes in the programming software, or decode the file further and update this section first.

## Housekeeping

`.DS_Store` files are ignored via `.gitignore`.
