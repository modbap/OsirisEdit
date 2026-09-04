# OsirisEdit

The modified wavetable and bank editor for the Osiris Eurorack synthesizer modules.

## Lineage & license

OsirisEdit is a **modified version of [WaveEdit](https://github.com/AndrewBelt/WaveEdit)** by
**Andrew Belt**, developed for **Synthesis Technology**. It inherits WaveEdit's license and is
released under the **GNU General Public License v3**.

- Copyright (C) 2021 Modbap Modular (Beatppl Inc.)
- Portions copyright (C) 2017 Andrew Belt, developed for Synthesis Technology

Full license text: [`LICENSE.txt`](LICENSE.txt) (byte-identical to upstream WaveEdit's).
Lineage, the GPL v3 section 5(a) statement of modifications, asset attribution and font notices:
[`NOTICE.md`](NOTICE.md).

The audio engine is unchanged from upstream. What this fork adds is Osiris-specific:
Osiris terminology, selectable wavetable length, the Convert / WavPak SD-card workflow, and
clipboard copy/paste across a whole wavetable.

**Neither Andrew Belt nor Synthesis Technology endorses, sponsors, or supports this fork, or is
responsible for it.** Report problems with OsirisEdit to Modbap Modular, not to the upstream
authors.

A browser edition built on the same lineage lives at
**[OsirisEditWeb](https://github.com/modbap/OsirisEditWeb)** (live at
[osirisedit.modbap.com](https://osirisedit.modbap.com)).

### Building

Make dependencies with

	cd dep
	make

Clone the in-source dependencies.

	cd ..
	git submodule update --init --recursive

Compile the program. The Makefile will automatically detect your operating system.

	make

Launch the program.

	./OsirisEdit

You can even try your luck with building the polished distributable. Although this method is unsupported, it may work with some tweaks to the Makefile.

	make dist
