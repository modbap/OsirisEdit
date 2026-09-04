# NOTICE

**OsirisEdit**
Copyright (C) 2021 Modbap Modular (Beatppl Inc.)
Portions Copyright (C) 2017 Andrew Belt, developed for Synthesis Technology.

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later
version. The full license text is in [`LICENSE.txt`](LICENSE.txt).

---

## 1. Upstream

OsirisEdit is a **modified version** of:

> **[WaveEdit](https://github.com/AndrewBelt/WaveEdit)**
> Copyright (C) 2017 Andrew Belt, developed for Synthesis Technology
> Licensed under the GNU General Public License v3

`LICENSE.txt` in this repository is byte-identical to upstream WaveEdit's
(`md5 d32239bcb673463ab874e80d47fae504`), so the license chain is intact.

**Neither Andrew Belt nor Synthesis Technology endorses, sponsors, or supports
this fork, or is responsible for it.** Problems with OsirisEdit should be
reported to Modbap Modular, not to the upstream authors. Their names appear here
only to give the credit the license requires.

---

## 2. Statement of modifications (GPL v3, section 5(a))

Changes made by Modbap Modular relative to upstream WaveEdit:

| File | Change |
|---|---|
| `src/OsirisEdit.hpp` | **Renamed** from upstream `src/WaveEdit.hpp`; every `#include` updated to match. Adds `<sndfile.h>`, the `Wave::saveWAV` and `Bank::saveWAV` overloads used by Convert, the `clipboardCopyAll` / `clipboardPasteAll` / `clipboardSetLength` declarations and `clipboardArrayActive`, and replaces the fixed `#define BANK_LEN 64` with a runtime `extern int BANK_LEN` plus `#define MAX_BANK_LEN 64` for selectable wavetable length. |
| `src/wave.cpp` | Adds `<iostream>`; adds a `Wave::saveWAV(const char *, SF_INFO, long bank_len, long wave_len)` overload; adds the clipboard array globals and `clipboardCopyAll` / `clipboardPasteAll` / `clipboardSetLength`. **No other change.** |
| `src/math.cpp` | Include line only (`WaveEdit.hpp` to `OsirisEdit.hpp`). **No other change.** |
| `src/ui.cpp` | Osiris terminology throughout the interface, and the Convert / WavPak workflow (`menuConvert`, "Separate Into WavPak Banks A - D") that writes SD-card-ready `A`/`B`/`C`/`D` folders. |
| `src/db.cpp` | Present in this fork and **not** in upstream's current master: the online wavetable-database browser (`dbInit` / `dbPage`), a libcurl + jansson client for the WaveEdit Online API. |
| Project files | `Makefile`, `Info.plist`, icons and logos renamed and rebranded for OsirisEdit. |

### The DSP is unchanged

The audio engine is **not** modified by this fork. The twelve effects and their
fixed order, the FFT conventions (RFFT scaled by `1/N`, pffft "ordered" packing,
harmonics as `magnitude x 2`), `cycle` and `normalize` are all exactly as in
upstream WaveEdit. The only differences in `wave.cpp` are the four additions
listed above, none of which touch the signal path.

---

## 3. Assets carried unchanged from upstream

The following are **byte-identical to upstream WaveEdit** and are
**Andrew Belt / Synthesis Technology content, not Modbap content**:

- `catalog/` : 43 WAV files across `00Digital`, `01Analog`, `02FM` and `03Glitch`
- `banks/` : 4 files (`ROM A.wav`, `ROM B.wav`, `ROM C.wav`, `Sines.wav`)

## 4. Fonts

`fonts/` contains **Lekton** (Regular, Bold, Italic), licensed under the
**SIL Open Font License**. The OFL text ships alongside the font files as
`fonts/SIL Open Font License.txt` and must travel with them in any
redistribution.

## 5. Build dependencies

OsirisEdit builds against third-party libraries that are fetched, not vendored
in this repository: **Dear ImGui**, **pffft**, **osdialog**, **lodepng** (Git
submodules under `ext/`), plus **SDL2**, **libsndfile**, **libsamplerate**,
**libcurl**, **jansson** and **zlib**. Each carries its own license; consult the
upstream projects. `LICENSE-dist.txt` covers the licenses that must accompany a
built distributable.

## 6. Web edition

A browser edition of this editor, built on the same lineage and licensed under
the same terms, is at **https://github.com/modbap/OsirisEditWeb**
(live at https://osirisedit.modbap.com). Its DSP core is a port of `src/wave.cpp`
and `src/math.cpp` from this repository.

## 7. Source availability

Complete corresponding source for this program is at
**https://github.com/modbap/OsirisEdit**.
Upstream source is at **https://github.com/AndrewBelt/WaveEdit** (GPL-3.0).

## 8. No warranty

This program is distributed in the hope that it will be useful, but **WITHOUT ANY
WARRANTY**; without even the implied warranty of **MERCHANTABILITY** or **FITNESS
FOR A PARTICULAR PURPOSE**. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this
program. If not, see <https://www.gnu.org/licenses/>.
