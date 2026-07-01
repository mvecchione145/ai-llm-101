# Why Bigger Models Need Bigger Hardware

![Placeholder: bar chart comparing memory needed — Gemma e2b (~3GB) vs Gemma 31B (~17-18GB) vs 70B model (~40GB) vs frontier 700B-1T model (hundreds of GB)](images/13-hardware-memory-chart.png)

- **Parameters** are roughly the number of knobs a model tuned during training.
- Gemma e2b: ~3GB · Gemma 31B: ~17–18GB · 70B model: ~40GB · Largest 2026 open models (700B–1T): hundreds of GB across enterprise GPUs
- **The "aha":** frontier models aren't secret code — they're often just too large to fit on a personal computer, so companies run them in data centers.

---

> Speaker notes: see [23:00–28:00 | Section 5: Live Demo](../lesson_outline.md#23002800--section-5-live-demo--running-an-open-model-yourself-ollama) in `lesson_outline.md`. Do not attempt to load a 70B+ model live.
