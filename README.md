![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg)

# PolyWave

- [Read the documentation for project](docs/info.md)

PolyWave is a GF180 Tiny Tapeout mixed-signal waveform source. A compact digital
engine generates four synchronized 16-bit sample streams, and the custom analog
layout converts them with four R-2R DAC ladders. The four analog outputs are
available on `ua[0]` to `ua[3]`.

## Project shape

This is a custom GDS/LEF submission, not a pure digital hardening flow. The
physical design is provided by the prebuilt files in `gds/` and `lef/`; the
GitHub action packages and checks those artifacts.

The Verilog in `src/project.v` documents and syntax-checks the digital
performance engine that drives the DAC ladders. Its extra `R2R_Bn_0` to
`R2R_Bn_3` output buses are internal mixed-signal layout connections to the four
16-bit R-2R ladders. They are intentionally not part of the normal Tiny Tapeout
digital-only wrapper interface.

The submitted analog frame still exposes the Tiny Tapeout `VAPWR` interface pin
because the physical GF180 pgvaa frame uses that template. The current digital
engine itself only uses the digital supply rails.

## Controls

In generated mode, `ui_in[7]` is low. `ui_in[5:4]` selects the live scene,
`ui_in[3]` selects the faster internal tempo, `ui_in[6]` freezes the phase
accumulators, and `ui_in[2:0]` plus `uio_in[7:0]` provide live modulation.

In direct DAC mode, `ui_in[7]` is high. `ui_in[5:4]` selects one of the four DAC
channels, `ui_in[3]` selects the low or high byte, `uio_in[7:0]` carries the byte
value, and a rising pulse on `ui_in[6]` loads that byte.

`uo_out[7]` reports the tempo tick, `uo_out[6:3]` reports the sequencer step, and
`uo_out[2:0]` mirrors the three live modulation bits.

## Resources

- [Tiny Tapeout analog specifications](https://tinytapeout.com/specs/analog/)
- [FAQ](https://tinytapeout.com/faq/)
- [Join the community](https://tinytapeout.com/discord)
