# 📝 Headroom Helper

**Headroom Helper** is a real-time, cross-platform performance analysis tool designed to identify system bottlenecks and provide actionable recommendations. It tracks key metrics like CPU/GPU usage, temperature, VRAM, and instantaneous frame time (latency) to analyze system constraints.

---

## ✨ Features

* **Real-time Metrics:** Tracks simulated CPU/GPU usage, temperature, VRAM consumption, and instantaneous frame time (latency).
* **Bottleneck Detection:** Diagnoses common issues like **GPU Bound**, **CPU Bound**, **Thermal Throttling**, and **VRAM Limits**.
* **Performance History:** Calculates **Average FPS** and **1% Low FPS** using a 30-second sliding window (`std::deque`) for stutter analysis.
* **Persistent Logging:** Writes critical events and warnings (like thermal spikes and VRAM limits) to **`headroom_log.txt`** for post-crash analysis.
* **Actionable Recommendations:** Prints specific advice based on the detected hardware bottleneck.

---

## 🚧 Library Integration Status (Future Work)

The current version uses **simulated data** within the `gather_metrics()` function. The next major development will involve integrating native OS APIs to obtain accurate real-time data.

| Platform | Target API / Method | Metrics Handled |
| :--- | :--- | :--- |
| **Windows** | **Performance Counters API (PDH)** or **WMI** | CPU/Memory/Temperatures (indirectly) |
| **Linux** | **`/proc`** and **`/sys` Filesystem Parsing** | CPU/Memory/Temperatures |
| **GPU Metrics** | **Vendor SDKs (e.g., NVAPI, AMD ADL)** | GPU Usage, VRAM, GPU Temperature |

---

## ⚙️ Prerequisites

* A C++ compiler (GCC, Clang, MSVC) that supports **C++11** or newer.

## 🔨 Building the Project

Assuming your source file is named `headroom_helper.cpp`:

```bash
# Example using g++ (Linux/macOS)
g++ headroom_helper.cpp -o headroom_helper -std=c++11
