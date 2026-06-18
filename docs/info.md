# PolyWave

A four-channel waveform generation system based on four 16-bit R-2R DACs. The design generates multiple synchronized analog signals that can be used for waveform synthesis, testing, modulation experiments and DAC characterization.

## How it works

The project contains four independent 16-bit R-2R DAC channels driven by digital waveform generators.

Each channel can generate different signal patterns derived from phase accumulators and digital synthesis logic. The generated digital values are converted to analog voltages by the corresponding R-2R ladder.

The outputs can be used individually or simultaneously to create multi-channel test signals, phase-shifted waveforms, modulation patterns, and other signal-processing demonstrations.

The design is intended as a compact mixed-signal laboratory showcasing the combination of digital waveform generation and high-resolution analog conversion.

## How to test

1. Apply power to the design.
2. Provide the system clock.
3. Observe the analog outputs on the available analog pins.
4. Verify that the outputs generate periodic waveforms.
5. Change the digital control inputs (if used) and verify that waveform frequency, phase, or operating mode changes accordingly.
6. Measure the analog outputs with an oscilloscope or data acquisition system to confirm correct DAC operation.

## External hardware

An oscilloscope, logic analyzer, or data acquisition system is recommended to observe the generated analog waveforms.
