### Arihanth Mutha

Co-founder of **Wet Loop**. We build developer tools for living-neuron computers:
hardware where cultured human neurons, grown on electrode arrays, do the computing.

The hardware exists today. The software layer for building applications on it mostly
doesn't. Developers wire application code, device interfaces, recording and evaluation
together by hand, then struggle to tell a real effect from a decoder quirk or a dropped
packet. That's the gap we work on.

#### What I'm building

| | |
|---|---|
| **wetloop** | The platform. One config and one session API for applications that run on living neurons (or a simulator), with deadline-bounded transport and fault accounting, sealed and replayable run records, counterbalanced comparison suites and reports that never label simulation as live biology. |
| **[dishsim](https://github.com/Arihanth-Mutha/dishsim)** · [live demo](https://arihanth-mutha.github.io/dishsim/) | A spiking neuronal culture on a 64-electrode array, in Rust → WebAssembly. Watch network bursts, stimulate electrodes, run a closed-loop task against controls in your browser. |
| **[spikeloop](https://github.com/Arihanth-Mutha/spikeloop)** | Real-time spike detection for multi-electrode arrays in Rust with Python bindings: 3 µs per 1 ms of 64-channel data, and artifact blanking so a stimulus never reads as a burst of spikes. |
| **[beatnull](https://github.com/Arihanth-Mutha/beatnull)** | Does your closed-loop result beat its controls? Block-level permutation tests, worst-case missing-data analysis, order-confound checks and pre-registered plans. Catches a "learning curve" made of pure noise. |

Together they cover one workflow, end to end. Each stands alone today, and dishsim's
experiments export straight into beatnull.

```
simulate the dish  →  detect spikes  →  run the experiment  →  check the result
     dishsim            spikeloop            wetloop               beatnull
```

#### How I work

- **Missing is not zero.** A dropped frame and a silent neuron are different facts, so
  they get recorded differently.
- **Blocks, not trials.** A thousand correlated trials are not a thousand samples.
- **Every control must be beaten,** and beating them still isn't proof that neurons
  learned.
- **Simulation is labelled as simulation.** Every report says what it does not show.

`Python` · `Rust` · `WebAssembly` · `TypeScript` · `numpy/scipy` · `PyO3`
