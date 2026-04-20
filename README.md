# 🎛️ SignalShift DSP Lab

**SignalShift DSP Lab** is a high-fidelity signal processing playground that explores the intersection of phase rotation and digital resolution. It generates white noise and subjects it to a continuous phase sweep while simultaneously degrading the "digital quality" (Sample Rate & Bit Depth) in synchronized cycles.

Built with a custom **Hilbert Transform FIR Filter**, it provides a real-time laboratory for understanding how audio analysis (FFT) and digital degradation affect signal integrity and phase.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Technology](https://img.shields.io/badge/Built%20With-Web%20Audio%20API-orange.svg)
![Status](https://img.shields.io/badge/Status-Advanced--Beta-green.svg)

---

## 📖 Product Overview

Most audio tools treat phase, sample rate, and bit depth as static settings. **SignalShift** treats them as dynamic variables. 

As the phase rotates from **-180° to +180°**, the engine cycles through different "Eras" of digital audio quality—moving from modern 24-bit/44.1kHz high-definition audio down to 4-bit/2kHz "Lo-fi" crunch. This allows engineers and researchers to hear and see (via the integrated oscilloscope) how aliasing and quantization noise interact with phase-shifted signals.

### The "Four Resolution" Cycle:
| Level | Quality | Sample Rate | Bit Depth | FFT Size |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Studio HD | 44.1 kHz | 24-bit | 512 |
| **2** | Standard | 22.05 kHz | 16-bit | 1024 |
| **3** | Vintage | 8.0 kHz | 8-bit | 2048 |
| **4** | Lo-Fi | 2.0 kHz | 4-bit | 4096 |

---

## ✨ Features

-   **360° Phase Rotation:** Uses a 31-tap Hilbert FIR filter to provide continuous, smooth phase shifting.
-   **Bitcrush Engine:** Real-time quantization to simulate Bit Depths from 24-bit down to a gritty 4-bit.
-   **Sample Rate Simulator:** Effective Sample & Hold downsampling to create authentic digital aliasing artifacts.
-   **Synchronized Parameter Cycling:** All parameters (Phase, Rate, Bits, FFT) are linked to a master "Update Frequency" (0.1Hz - 10Hz).
-   **Real-time Oscilloscope:** A high-speed canvas visualizer showing the "stair-step" effect of low bit/rate settings in real-time.
-   **Pure Vanilla JS:** No libraries or frameworks. Runs in any modern browser via the Web Audio API.

---

## 🗺️ Roadmap

- [ ] **Stereo Decorrelation:** Independent phase rotation for Left and Right channels to test stereo imaging.
- [ ] **Noise Coloring:** Toggle between White, Pink, and Brown noise.
- [ ] **Manual Lock Mode:** Allow users to "freeze" the cycle on a specific bit depth or sample rate.
- [ ] **Spectrogram View:** A waterfall frequency display to visualize aliasing folds in the high frequencies.
- [ ] **IR Export:** Export the current state as a short Impulse Response WAV file.

---

## 🚀 Hosting Options

SignalShift is a self-contained Single Page App (SPA).

| Provider | Type | Cost | Pros |
| :--- | :--- | :--- | :--- |
| **GitHub Pages** | Static | **Free** | Best for version control integration. |
| **Cloudflare Pages** | Static | **Free** | Superior global edge performance. |
| **Netlify** | Static | **Free** | Extremely fast "drag-and-drop" deployment. |
| **Self-Hosted** | Static | Variable | Total privacy and control over headers. |

---

## 🛠️ Technical Deep-Dive

### The Phase Rotator
The app implements a **Quadrature Splitter**. The source signal is split into two paths:
1.  **I (In-phase):** A simple delay line (15 samples) to match filter latency.
2.  **Q (Quadrature):** A 31-tap Hilbert Transform FIR filter that shifts all frequencies by 90°.
By modulating the gain of **I** with $\cos(\theta)$ and **Q** with $-\sin(\theta)$, we achieve a perfect mathematical phase rotation.

### The Downsampler & Bitcrusher
These are implemented inside a `ScriptProcessorNode`. 
*   **Downsampling** is achieved via "Sample and Hold": the algorithm only captures a new input sample once the hardware clock has passed the threshold of the "Target Rate."
*   **Bitcrushing** is achieved by normalizing the signal to a range, multiplying by the bit-step count ($2^{bits}$), rounding to the nearest integer, and then re-normalizing.

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.
