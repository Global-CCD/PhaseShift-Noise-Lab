# 🌌 PhaseShift Noise Lab

**PhaseShift Noise Lab** is a high-precision, browser-based signal processing utility that generates white noise and applies a continuous 360-degree phase rotation. By utilizing a 31-tap Hilbert Transform FIR filter, the app achieves real-time phase shifting, providing a unique tool for audio engineers, acoustic testing, and DSP enthusiasts.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Technology](https://img.shields.io/badge/Built%20With-Web%20Audio%20API-orange.svg)
![Status](https://img.shields.io/badge/Status-Production--Ready-green.svg)

---

## 📖 Product Overview

Unlike standard noise generators, **PhaseShift Noise Lab** focuses on the spatial and mathematical properties of sound. The application creates a "rotating" stereo-compatible mono signal that sweeps from -180° to +180° in a continuous loop. 

To visualize the impact of these phase shifts and processing overhead, the app dynamically cycles through different FFT (Fast Fourier Transform) analysis sizes, allowing users to observe how window lengths affect signal representation in real-time.

### Use Cases:
*   **Acoustic Testing:** Test phase cancellation and room nodes with moving-phase noise.
*   **DSP Education:** Visualize how Hilbert Transforms and FIR filters manipulate signals.
*   **Audio Gear Calibration:** Check how hardware or software plugins handle rapid phase transitions and varying FFT resolutions.

---

## ✨ Features

-   **Precision White Noise:** Mathematically generated white noise buffer for uniform spectral density.
-   **Hilbert Transform Rotator:** Employs an analytic signal approach using a 31-tap finite impulse response (FIR) filter.
-   **Continuous Phase Sweep:** Automated looping from -180° $\rightarrow$ 0° $\rightarrow$ +180° $\rightarrow$ -180°.
-   **Dynamic FFT Scaling:** Automatically switches between four standard analyzer sizes (512, 1024, 2048, 4096) to demonstrate frequency resolution vs. time resolution.
-   **Variable Update Rates:** User-selectable control frequencies (0.1Hz to 10Hz) for phase and FFT transitions.
-   **Zero Dependencies:** Built entirely with vanilla JavaScript and the Web Audio API. No frameworks, no bloat.

---

## 🗺️ Roadmap

- [ ] **Custom Noise Colors:** Add Pink, Brown, and Blue noise generation.
- [ ] **Stereo Decorrelation:** Option to rotate Left and Right channels at different frequencies for wide-field spatial testing.
- [ ] **Manual Override:** Toggle between "Auto-Sweep" and "Manual Phase Control" via a slider.
- [ ] **Spectrogram View:** Add a 2D heat-map spectrogram to visualize frequency density alongside the oscilloscope.
- [ ] **WAV Export:** Record a 10-second loop of the processed signal for use in DAWs.

---

## 🚀 Hosting Options

Because this is a Single Page Application (SPA) consisting of a single HTML file, it can be hosted on almost any static platform.

| Provider | Type | Cost | Pros | Cons |
| :--- | :--- | :--- | :--- | :--- |
| **GitHub Pages** | Static | **Free** | Integrated with your repo; incredibly simple setup. | No server-side logic (not needed for this app). |
| **Cloudflare Pages** | Static | **Free** | Blazing fast CDN; unlimited bandwidth; edge caching. | None for this specific use case. |
| **Cloudflare Workers** | Edge Computing | Free Tier / Paid | Can inject logic or headers at the edge. | Overkill for a single HTML file. |
| **Netlify** | Static | Free Tier | Excellent developer experience; drag-and-drop deploy. | Bandwidth limits on the free tier (100GB). |
| **Vercel** | Static/Serverless | Free Tier | Optimized for modern JS frameworks. | Geared more toward Next.js/React. |
| **Self-Hosted (VPS)** | Managed | Paid ($5+/mo) | Full control over headers and environment. | Requires maintenance and security patching. |

### 🛠️ Recommendation
*   **For most users:** **GitHub Pages** is the best choice for seamless integration with your source code.
*   **For maximum performance:** **Cloudflare Pages** offers the best global latency and DDoS protection.

---

## 🛠️ Quick Start

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/phaseshift-noise-lab.git
    ```
2.  **Open the file:**
    Simply double-click `index.html` in your browser.
3.  **Interact:**
    Click **"Start Audio"** (Browsers block audio until a user gesture occurs).

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

---

*Developed with ❤️ for the Audio Engineering Community.*
