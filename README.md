# 🔋 Energy Optimizations for Memory Architectures — A Survey
[![Paper](https://img.shields.io/badge/Paper-PDF-red)](./paper.pdf)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](#license)
[![Built-with](https://img.shields.io/badge/Built%20with-Markdown-blue)](#)

A practical + research survey spanning hardware, software, and system-level methods to cut energy while preserving performance—from **NVM-based in-memory computing (IMC)** to **cache tuning**, **real-time NVM memory designs**, **HPC scheduling (Deviation Backfilling + kNN)**, and **Python distributed-compute optimizations (SharedArray in PyCOMPSs)**.

---

## 🧭 TL;DR
- **Hardware:** Racetrack & RRAM for **IMC**, hybrid banked NVM, DVFS, and clock gating.
- **Architecture/SoC:** **TECH-DoE** cache tuning; banked NVM + write buffer to improve WCET predictability.
- **Systems:** **Deviation Backfilling** schedules HPC jobs more efficiently/fairly with **kNN runtime prediction**.
- **Software:** Shared memory for Python (**SharedArray + PyCOMPSs**) to reduce copies and speed up data-heavy tasks.

---

## 📑 Table of Contents
- [Motivation](#motivation)
- [Key Contributions](#key-contributions)
- [What’s Inside](#whats-inside)
- [Highlights by Layer](#highlights-by-layer)
- [Figures & Diagrams](#figures--diagrams)
- [Who Should Read This](#who-should-read-this)
- [Quick Start (Repo Structure)](#quick-start-repo-structure)
- [How to Cite](#how-to-cite)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## 💡 Motivation
Modern compute spans **edge → embedded → HPC** and is constrained by power, thermals, and cost. Traditional “perf-first” designs hit a wall; we need **cross-layer** energy strategies that still ship real-time guarantees, throughput, and fairness.

---

## 🧩 Key Contributions
1. **NVM for IMC:** Survey of **Racetrack** & **RRAM** devices/arrays and the IMC architectures that exploit them.
2. **Predictable Real-Time NVM:** **Banked NVM + write buffer + flush primitive** to mask NVM writes and tighten **WCET** bounds.
3. **Cache Energy Tuning:** **TECH-DoE**: a design-of-experiments heuristic to converge to near-Pareto cache configs with low search cost.
4. **HPC Scheduling:** **Deviation Backfilling** with **kNN** runtime prediction to balance utilization and fairness.
5. **Python at Scale:** **SharedArray + PyCOMPSs** integration to enable true system-wide shared memory for data-intensive tasks.

---

## 📦 What’s Inside
- `paper.pdf` — Full survey (with figures and references).
- `figures/` — Raw diagrams (placeholders to recreate Fig. 1.0, 1.2, 1.3).
- `notes/` — One-pagers for each technique (summaries + “when to use” guidance).
- `extras/` — BibTeX, slide templates, and reading list.

> Tip: If you add code later (e.g., cache-tuning notebooks, kNN runtime predictor demos), create `code/tech-doe/`, `code/hpc-scheduling/`, etc.

---

## 🧱 Highlights by Layer

### Hardware & Devices
- **Racetrack / RRAM IMC:** Reduces data movement; co-optimization (device non-idealities → array/arch mapping).
- **Hybrid NVM:** Banked organization to amortize write costs and reduce leakage.

### Architecture & SoC
- **TECH-DoE Cache Tuning:** 2^k factorial DoE to rank sensitivity (size, line, assoc.) → iterate to a low-energy cache config.
- **WCET-Aware NVM Subsystem:** Write buffer + banked NVM + `flush` instruction → predictable timing with better performance/energy.

### Systems & Schedulers
- **Deviation Backfilling (HPC):** Uses **kNN** to estimate job runtimes; computes a deviation-based delay threshold → higher throughput with fairness.

### Software & Frameworks
- **SharedArray + PyCOMPSs:** System-wide shared NumPy buffers for multi-process reuse (less copy/serialize) → meaningful speedups for high-reuse workloads (e.g., k-means).

---

## 🖼 Figures & Diagrams
- **Fig 1.0** — Nanowire + vertical MTJ (conceptual Racetrack cell)  
- **Fig 1.2** — **WCET estimation flow** with banked NVM + write buffer  
- **Fig 1.3** — **EASY vs Deviation Backfilling** timeline comparison  

> Recreate these in `figures/` (SVG/PNG) so GitHub renders them inline.

---

## 👩‍🔧 Who Should Read This
- **FPGA/SoC/ASIC** engineers exploring low-power memory subsystems and IMC.
- **Real-time embedded** devs needing **predictable** memory timing on NVM.
- **HPC practitioners** seeking scheduling policies that are both **efficient** and **fair**.
- **Python/Distributed** engineers optimizing shared data paths and cluster throughput.



---

### What I pulled directly from your paper
- Scope: NVM/IMC (Racetrack, RRAM), PyCOMPSs + SharedArray integration, **Deviation Backfilling + kNN**, TECH-DoE cache tuning, WCET with banked NVM + write buffer, plus figures (nanowire/MTJ, WCET flow, backfilling comparison). See your uploaded PDF for details.

If you want, I can also:
- Generate **SVG figures** for Fig 1.0 / 1.2 / 1.3 (so they render cleanly on GitHub).
- Add **one-page summaries** for each technique under `notes/`.
- Create a **slide deck** (`extras/slides.pptx`) auto-filled with the highlights.


---

## 🚀 Quick Start (Repo Structure)
