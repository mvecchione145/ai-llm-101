# ai-llm-101

A 30-minute talk for a general audience explaining AI, machine learning, and LLMs from the ground up — no technical background assumed. Ends with a live demo of running an open-source model locally.

_Last updated: 2026-07-01_

## Contents

- [`docs/lesson_outline.md`](docs/lesson_outline.md) — full speaker script with timing, talking points, an optional deep-dive analogy, a live-demo walkthrough, and an FAQ of key terms (neural network, vector, parameter, agent, and more).
- [`docs/slides/`](docs/slides/) — the slide deck as one markdown file per slide, with image placeholders for you to fill in. See [`docs/slides/README.md`](docs/slides/README.md) for the deck order and full image list.

## What it covers

1. **The AI landscape** — how AI, machine learning, deep learning, and LLMs nest inside one another.
2. **What an LLM is actually doing** — tokenization, vectors, and next-token prediction.
3. **RAG (Retrieval-Augmented Generation)** — how models stay grounded in current, specific information.
4. **The current landscape** — a factual, even-handed tour of today's chatbots, open-source models, and the tools built on them.
5. **Live demo: running an open model yourself** — using [Ollama](https://ollama.com) to show a model running entirely on a laptop, then contrasting it with the hardware frontier models require.

## Live Demo

The talk's centerpiece is running a small open-source model locally with Ollama.

**Before presenting**, install Ollama and pre-pull the demo model so you're not waiting on venue Wi-Fi:

```sh
# Install Ollama: https://ollama.com
ollama pull gemma4:e2b
```

**During the talk**, run it live:

```sh
ollama run gemma4:e2b
```

See [`docs/lesson_outline.md`](docs/lesson_outline.md#23002800--section-5-live-demo--running-an-open-model-yourself-ollama) for the full walkthrough, talking points, and backup-plan notes.

## License

[MIT](LICENSE)
