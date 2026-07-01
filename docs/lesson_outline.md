# Understanding LLMs
**30-minute talk — general audience, no tech background assumed**

---

## 0:00–2:00 | Welcome & Framing

- Thank people for coming, introduce yourself briefly.
- Set expectations: "By the end of 30 minutes, you'll understand what people mean when they say AI, machine learning, and LLM — and we'll see it in action."
- One reassuring line up front: "None of this requires a technical background — if you can follow a recipe, you can follow this."

---

## 2:00–7:00 | Section 1: The AI Landscape

**Key visual: nested circles — AI → Machine Learning → Deep Learning → LLM**

Talking points:
- **AI (Artificial Intelligence)** is the broadest term — any system designed to perform tasks that normally require human intelligence. This covers a huge range: your GPS finding a route, a spam filter, a video game opponent, a chatbot. Not all AI "learns" — some of it is just carefully programmed rules (e.g., an old-school chess program that follows a fixed set of strategies).
- **Machine Learning (ML)** is a subset of AI — specifically, systems that improve by learning patterns from data rather than being explicitly programmed rule by rule. Example: a system that learns to recognize spam by seeing thousands of examples of spam vs. non-spam.
- **Deep Learning (DL)** is a subset of ML — it uses neural networks with many layers ("deep" = many layers) loosely inspired by how neurons connect in the brain. Older ML techniques (like decision trees or linear regression) are ML but not "deep."
- **Large Language Model (LLM)** is a subset of Deep Learning — specifically, deep neural networks (using an architecture called a "transformer") trained on massive amounts of text to work with human language.

> Slide idea: four nested circles, labeled AI → ML → DL → LLM, largest to smallest.

> **Optional deeper analogy — "Deep learning as finding the best-fit line"** (use this if you want to spend an extra minute or two building real intuition for *how* learning works, not just what the nesting diagram looks like):
>
> This is a simplification, but an honest one — the core mechanic really is shared between basic statistics and deep learning: adjust internal numbers until they best match the patterns in the data.
>
> 1. **Start simple:** Show a 2D scatter plot of random data points with a single straight best-fit line through them (classic linear regression). Explain: "This line has just two adjustable numbers — its slope and starting point. 'Fitting' the line means nudging those two numbers until it sits as close as possible to all the points. That 'nudge the numbers until it fits' process is the same basic idea behind training any machine learning model — deep learning included."
> 2. **Add complexity:** Now show a data set that curves, where a straight line clearly fits poorly. Introduce a curved line (a simple polynomial) that bends to follow the data instead. Point out: "To fit a more complex pattern, we needed a more flexible shape — and that took more adjustable numbers to describe the curve." (This is a nice callback to the "parameters" definition in the FAQ below.)
> 3. **Go further:** Real-world data — a photo, a sentence, a sound clip — is far too complex to describe with one curve, and it lives in far more than two dimensions. This is where deep learning comes in: instead of one flexible curve, a deep neural network chains together many simple mathematical "bends" (layers), each nudging the data a little, so that combined they can approximate extremely complex patterns no single equation could capture. That's the "deep" in deep learning — many layers stacked, each contributing a small transformation.
> 4. **Honest caveat, if asked:** Real neural networks aren't literally drawing lines or curves on a 2D graph — they operate across many more dimensions, and each layer applies a non-linear transformation, not just a bend. But the underlying principle — adjusting internal numbers so the model's output best matches patterns in its training data — is genuinely the same idea as fitting a line to points, just scaled up enormously.
>
> *Visual sequence for slides: (1) scatter plot + straight line → (2) same scatter plot + curved line → (3) an abstract "many small bends stacked together" illustration or simple layered-network diagram, building visually from simple to complex.*

---

## 7:00–15:00 | Section 2: What Is an LLM Actually Doing?

Talking points (build this step-by-step, it's the technical heart of the talk):

1. **Tokenization** — The model breaks your text into small chunks called *tokens*. These aren't always whole words — "unbelievable" might split into "un" + "believ" + "able." This step is mechanical; the tokens don't carry meaning yet on their own.
2. **Turning tokens into numbers** — Each token gets converted into a list of numbers (a "vector") that the neural network can process. The network then uses its trained layers to figure out how tokens relate to each other and what they mean in context.
3. **Predicting the next token** — The model looks at everything so far and calculates the most probable *next* token. It adds that token to the sequence, then repeats the entire process again for the next one — one token at a time — until the response is complete.

> Optional Q&A nugget (only bring up if asked "why does it give different answers to the same question?"): models usually don't always pick the single most likely token — they add a small amount of controlled randomness so responses don't feel robotic or identical every time.

**Live demo moment:** Ask ChatGPT or Claude a simple question live, and narrate: "Watch — it's not searching a database for a memorized answer, it's generating this response one token at a time, live, right now."

---

## 15:00–19:00 | Section 3: RAG (Retrieval-Augmented Generation)

Talking points:
- LLMs only know what they were trained on, and that training has a cutoff date — they don't automatically know about your library's catalog, today's news, or your company's internal documents.
- **RAG** solves this: before generating a response, the system first *retrieves* relevant information (from a database, a set of documents, or the web) and hands that to the LLM as extra context, so its answer is grounded in current, specific, relevant information — not just what it memorized during training.
- Simple analogy: it's like giving someone an open-book exam instead of asking them to answer purely from memory.

**Live demo moment (optional, if time allows):** Ask a question that requires current information (e.g., today's weather or a recent event) to show the model searching before answering.

---

## 19:00–23:00 | Section 4: The Current Landscape of Offerings

Keep this factual and even-handed — no endorsements, just an overview of categories:

- **General-purpose chatbots/assistants:** ChatGPT (OpenAI), Claude (Anthropic), Gemini (Google), Copilot (Microsoft), Meta AI (Meta).
- **Open-source / downloadable models:** Meta's Llama family, Mistral, Google's Gemma, Alibaba's Qwen, DeepSeek, and others — models people can download and run themselves rather than only through a web app.
- **Specialized tools built on these models:** coding assistants (GitHub Copilot, Claude Code), and productivity integrations (AI features now built into Word, Gmail, Excel).
- **Common thread:** most of these products are the same underlying idea (an LLM, sometimes with RAG or agent capabilities) packaged for a specific use case.

> Bridge line into the demo: "That 'open-source / downloadable' category isn't theoretical — I can actually show you one running, right here, on this laptop."

**Detailed reference table** (useful as a handout, backup slide, or just your own cheat sheet — probably too dense to put on a single presentation slide as-is):

| Company | LLM | Tool / Product | Description |
|---|---|---|---|
| Anthropic | Claude (Opus, Sonnet, Haiku) | Claude.ai, Claude Code | General-purpose chatbot assistant, plus a dedicated coding agent (Claude Code) built on the same models. |
| OpenAI | GPT-5 family | ChatGPT, Codex | The original mainstream chatbot; Codex is OpenAI's agentic coding tool built on the same models. |
| Google | Gemini | Gemini app, Google Workspace (Docs, Gmail, Search) | Multimodal chatbot integrated directly into Google's search engine and productivity apps. |
| Google | Gemma | Downloadable (via Ollama, Hugging Face, etc.) | Google's separate, fully open-weight model family — distinct from Gemini, meant for anyone to download and run themselves. |
| Meta | Llama 4 | Meta AI (in WhatsApp, Instagram, Facebook), downloadable | Open-weight model family; the Meta AI app is the consumer-facing chatbot built on it. |
| Microsoft | GPT-5 family (via OpenAI partnership) | Copilot (Word, Excel, Windows, Teams) | AI features woven directly into Microsoft's productivity software rather than a separate standalone chatbot. |
| Mistral AI | Mistral (Large, Small) | Le Chat | French AI lab; offers a mix of open-weight and proprietary models. |
| Alibaba | Qwen | Downloadable, Alibaba Cloud | Open-source model family with especially strong multilingual support. |
| DeepSeek | DeepSeek (V and R series) | Downloadable, DeepSeek app | Chinese open-weight lab known for very large, cost-efficient models. |

> **Heads up:** exact model version numbers (e.g., "GPT-5 family," "Claude Opus/Sonnet/Haiku") shift roughly monthly across every one of these companies — that's normal in this industry, not something you're missing. Worth a quick sanity check of company names/products (not necessarily exact version numbers) a day or two before you present, since a name could plausibly change between now and then.

---

## 23:00–28:00 | Section 5: Live Demo — Running an Open Model Yourself (Ollama)

**Goal of this section:** prove open-source models are real and runnable on ordinary hardware, then show *why* the highest-performing models still require serious infrastructure — setting up the "why does ChatGPT need a data center?" payoff.

**Before the talk (prep, not to be done live):**
- Install Ollama ahead of time (ollama.com — one-line installer for Mac/Windows/Linux).
- Pre-download ("pull") the small model you'll demo so you're not waiting on library Wi-Fi during the talk: `ollama pull gemma4:e2b` (about 3GB — runs comfortably on almost any modern laptop, no dedicated GPU needed).

**Live steps:**
1. Open a terminal and run: `ollama run gemma4:e2b`, then ask it a question live (e.g., "What's a good book for a rainy day?").
2. Call out explicitly: "This is Gemma — Google's open-source model family. It's a separate line from Gemini, Google's flagship product; Gemma is fully open-weight, meaning anyone can download and run it themselves, which is exactly what we're doing right now."
3. Narrate while it responds: "This is running entirely on my laptop — not the internet. If I turned off Wi-Fi right now, it would still work." (Turning off Wi-Fi live is a nice, low-risk flourish if you're comfortable with it.)
4. Point out the size: this model has about 2 billion "effective" parameters — tiny compared to the frontier models people read about.

**The contrast — why bigger models need bigger hardware:**
- A model's "parameters" are roughly the number of knobs it learned to tune during training. More parameters generally means more capability, but also means the model takes up more memory.
- Even staying within just the Gemma family, the difference is stark: the small edge model we just ran needs about 3GB of memory, while Google's own flagship Gemma model (31 billion parameters) needs around 17-18GB — and that's still Google intentionally keeping a version small enough for a high-end consumer GPU.
- Go outside the Gemma family to the true frontier, and the numbers jump again: as a rough rule of thumb, a 70-billion-parameter model needs around 40GB of memory to run well (that figure assumes a compressed/"quantized" version — see the aside below; a full-precision 70B model would need closer to 140GB) — more than any consumer graphics card has on its own (high-end consumer GPUs typically top out around 32GB, e.g. the RTX 5090).
- The very largest open models being released in 2026 — like Kimi K2.6 or DeepSeek's largest models — have around 700 billion to 1 trillion parameters. Running those requires hundreds of gigabytes of memory spread across multiple enterprise-grade GPUs, hardware that costs tens of thousands of dollars and lives in data centers, not living rooms.
- **This is the "aha": it's not that ChatGPT, Claude, or Gemini's best models are secretly special code — often they're just too large to fit on a personal computer, so the company runs them in a data center and lets you access them over the internet instead.**

> Optional aside if there's time/interest: mention "quantization" — a technique that shrinks a model's memory footprint (like compressing a photo) at a small cost to quality, which is how some larger models get squeezed onto consumer hardware. Not essential to the core point — skip if running short on time.

---

## 28:00–31:00 | Wrap-Up & Q&A

- Recap the nesting: AI → ML → DL → LLM, plus RAG as an extension on top of an LLM, and the local-vs-cloud tradeoff from the Ollama demo.
- Open the floor for questions — this is often where the most engagement happens for a general audience. (If someone asks about "AI agents," you have a ready answer in the FAQ below.)
- Optional takeaway line: "The core idea — predicting the next word based on patterns — is simple. Everything impressive you see built on top of it (search, tool use, and the sheer scale of these models) is what makes it feel more powerful."

---

### Speaker Notes
- **Total is now ~31 minutes.** If you need to hold to exactly 30, cut in this order: (1) drop the optional RAG live demo — already marked optional, (2) skip the quantization aside in the Ollama section, (3) trim Section 1's "not all AI learns" tangent.
- The Ollama demo is the one section where a live failure is genuinely possible (Wi-Fi, laptop performance, projector/terminal font size). Pre-pull the model, test the exact terminal font/size on the projector beforehand, and consider a backup screen-recording of the demo working, just in case.
- Do **not** attempt to actually load a 70B+ model live to "prove" it's too big — it may hang or crash without a clear payoff. The size comparison lands fine as a stated fact; no need to demonstrate the failure itself.
- Build in a 2-3 minute buffer since audience questions often come up mid-section for a topic like this.

---

## FAQ: Key Terms Explained

Handy if these come up during Q&A, or if you'd like to fold a definition into a slide.

**Q: What is a neural network?**
A neural network is a computing system loosely inspired by how neurons connect in the brain. It's organized in layers: an input layer, one or more "hidden" layers in between, and an output layer. Each connection between layers has a numerical "weight" that controls how much one piece of information influences the next. Data flows through the network layer by layer, getting transformed each step, until it comes out the other end as a prediction or response. "Deep" learning simply means a network with many hidden layers stacked together — the more layers, the more complex the patterns it can learn.
> Analogy: think of it like an elaborate assembly line, where each station makes a small adjustment to the item passing through. A "deep" network just has a lot of stations.

**Q: What is a vector?**
A vector is a list of numbers used to represent something — in an LLM's case, a token — as a point in space, so the computer can do math on it. Tokens with similar meanings end up as vectors that are numerically "close" to each other, which is how the model captures relationships between words mathematically rather than just matching text.
> Analogy: imagine giving every word GPS coordinates on a giant "meaning map." Words with related meanings (like "king" and "queen") end up near each other on that map, while unrelated words (like "king" and "bicycle") land far apart.

**Q: What is a model parameter?**
A parameter is one of the individual numerical values inside a neural network — the "weights" mentioned above — that gets adjusted during training. Think of each parameter as a small dial the model learns to turn to just the right setting so it produces good outputs. When you hear a model "has 70 billion parameters," that means it has 70 billion of these tunable dials. More parameters generally give a model more capacity to capture complex patterns — which is part of why bigger models can be more capable, but also why they need so much more memory to run (this ties directly into the Ollama demo above).
> Analogy: like a massive soundboard with billions of tiny sliders, each nudged to a precise position during training so that, combined, they produce the right output for a given input.

**Q: What is an agent?**
A regular chatbot just talks — it responds with text, but can't *do* anything beyond that. An "agent" extends an LLM by giving it tools: the ability to search the web, run code, browse a website, or call other software. It works in a loop — take an action, look at the result, decide the next step, repeat — continuing until it reaches its goal or hits a stopping point (like a step limit). "Autonomous" sounds more dramatic than it usually is in practice: agents can only do what their given tools allow, and most real-world uses still include guardrails or a human checking in before anything important happens.
> Analogy: think of a regular chatbot as a knowledgeable person answering questions over the phone — they can tell you what to do, but can't do it themselves. An agent is like handing that same person a set of keys and letting them actually go complete the task, checking back in with you as they go.

**Q: How does image generation work?**
Briefly: it's a different technology from LLMs. Most image generators start with a canvas of random visual "noise" and gradually clean it up, step by step, into a coherent picture that matches your text description — a process called diffusion. (Kept short on purpose — happy to expand this into its own section if you ever want to cover it in a future talk.)

**Q: What is contained in an LLM model file?**
A model file bundles everything needed to run the model: the weights (the billions of learned parameter values — the bulk of the file size), metadata describing the architecture (how many layers, attention heads, etc.), and the tokenizer/vocabulary for converting text to tokens and back. Ollama's format (GGUF) packages all of this into a single self-contained file — that's literally what gets downloaded when you run ollama pull.

> Analogy: like a shipped IKEA box that contains the parts (weights), the assembly instructions (architecture metadata), and the glossary of part names (tokenizer) all in one package, instead of needing three separate boxes.