# Appendix: Why Do Bigger Models Need Bigger Hardware?

![Placeholder: bar chart comparing memory needed — Gemma e2b (~3GB) vs Gemma 4 31B (~17-18GB) vs 70B model (~40GB) vs frontier 700B-1.6T model (hundreds of GB)](images/16-hardware-memory-chart.png)

- **Parameters** are roughly the number of knobs a model tuned during training.
- Gemma e2b: ~3GB · Gemma 4 (31B): ~17–18GB · 70B model: ~40GB · Largest 2026 open models (700B–1.6T): hundreds of GB across enterprise GPUs
- Figures assume 4-bit quantization; a full-precision 70B model would need closer to 140GB. Consumer GPU ceiling is now ~32GB (e.g. RTX 5090), up from the 24GB ceiling of the prior generation.

> The "aha": frontier models aren't secret code — they're often just too large to fit on a personal computer, so companies run them in data centers instead.

[← Previous: Appendix: Parameter](15-appendix-parameter.md) · [Next: Appendix: Agent →](17-appendix-agent.md)
