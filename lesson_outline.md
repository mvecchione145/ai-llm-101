# Understanding LLMs
**30-minute talk — general audience, no tech background assumed**

---

## 0:00–2:00 | Welcome & Framing

- Thank people for coming, introduce yourself briefly.
- **Opening hook (rhetorical or polling question):** "How many of you have asked ChatGPT or Claude something and wondered how it actually comes up with an answer?" (a show of hands works well here — makes the room part of the talk immediately instead of a lecture).
- Set expectations: "By the end of 30 minutes, you'll understand what people mean when they say AI, machine learning, and LLM — and we'll see it in action."
- **Name the structure out loud** (audiences retain a named structure noticeably better than an unstructured talk): "Here's the shape of the next 30 minutes — first what these things actually are, then why it matters to you, then how you can go try one yourself tonight." That's What?–So What?–Now What?, and it maps directly onto Sections 1–2 / Sections 3–4 / wrap-up below.
- One reassuring line up front: "None of this requires a technical background — if you can follow a recipe, you can follow this."

---

## 2:00–7:00 | Section 1: The AI Landscape

**Key visual: nested circles — AI → Machine Learning → Deep Learning → LLM**

Talking points:
- **AI (Artificial Intelligence)** is the broadest term — any system designed to perform tasks that normally require human intelligence. This covers a huge range: your GPS finding a route, a spam filter, a video game opponent, a chatbot. Not all AI "learns" — some of it is just carefully programmed rules (e.g., an old-school chess program that follows a fixed set of strategies).
- **Machine Learning (ML)** is a subset of AI — specifically, systems that improve by learning patterns from data rather than being explicitly programmed rule by rule. Example: a system that learns to recognize spam by seeing thousands of examples of spam vs. non-spam.
- **Deep Learning (DL)** is a subset of ML — it uses neural networks with many layers ("deep" = many layers) loosely inspired by how neurons connect in the brain. Older ML techniques (like decision trees or linear regression) are ML but not "deep."
- **Large Language Model (LLM)** is a subset of Deep Learning — specifically, deep neural networks (using an architecture called a "transformer") trained on massive amounts of text to work with human language.

---

## 7:00–15:00 | Section 2: What Is an LLM Actually Doing?

Talking points (build this step-by-step, it's the technical heart of the talk):

1. **Tokenization** — The model breaks your text into small chunks called *tokens*. These aren't always whole words — "unbelievable" might split into "un" + "believ" + "able." This step is mechanical; the tokens don't carry meaning yet on their own.
2. **Turning tokens into numbers** — Each token gets converted into a list of numbers (a "vector") that the neural network can process. The network then uses its trained layers to figure out how tokens relate to each other and what they mean in context.
3. **Predicting the next token** — The model looks at everything so far and calculates the most probable *next* token. It adds that token to the sequence, then repeats the entire process again for the next one — one token at a time — until the response is complete.

> Optional Q&A nugget (only bring up if asked "why does it give different answers to the same question?"): models usually don't always pick the single most likely token — they add a small amount of controlled randomness so responses don't feel robotic or identical every time.

> Optional philosophical aside (only bring up if someone asks "but does it actually *understand* what it's saying?"): this is a great moment to mention the **Chinese Room argument** — see the FAQ below for the full version.

**Live demo moment:** Ask ChatGPT or Claude a simple question live, and narrate: "Watch — it's not searching a database for a memorized answer, it's generating this response one token at a time, live, right now."

> **Optional deeper analogy — "Deep learning as finding the best-fit line"** (use this if you want to spend an extra minute or two building real intuition for *how* the model learned to do what you just described, not just what the mechanics look like):
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
- **Why this matters, not just what exists:** these tools already save people real hours a week on writing, research, and coding — and the open-weight row on the table below (Llama, Gemma, Qwen, DeepSeek) means access isn't gated behind a subscription; anyone with an ordinary laptop can run one — see the FAQ below if asked how, or why the biggest models still need a data center.

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

## 23:00–26:00 | Wrap-Up & Q&A

- Recap the nesting: AI → ML → DL → LLM, plus RAG as an extension on top of an LLM.
- **Close on a call to action, not just a recap:** "Ollama is free, takes about five minutes to install, and lets you run one of these models yourself, right on your laptop — try it tonight." This is the "Now What" payoff — give the audience something to actually do with what they just learned, not just a summary of it.
- Open the floor for questions — this is often where the most engagement happens for a general audience. (If someone asks about "AI agents" or why bigger models need bigger hardware, you have ready answers in the FAQ below.)
- Optional takeaway line: "The core idea — predicting the next word based on patterns — is simple. Everything impressive you see built on top of it (search, tool use, and the sheer scale of these models) is what makes it feel more powerful."

---

### Speaker Notes
- **Total is now ~26 minutes**, leaving a few minutes of slack under the 30-minute target for Q&A to run long — a comfortable position to be in.
- Build in a 2-3 minute buffer since audience questions often come up mid-section for a topic like this.
- **Delivery mechanics:** watch for hedges ("I think," "sort of," "kind of") and tag questions ("...right?") — swap for assertive phrasing ("I believe," "one way to think about it"). Land sentences by exhaling fully at the end rather than trailing off or up-talking into a question mark.
- **If you go blank mid-section:** paraphrase what you just said, ask the room a rhetorical question, or return to the core "predicting the next token" theme to regain your footing — don't panic-fill with filler words.
- **Practice standing up, out loud,** section by section — not mental rehearsal, and not memorizing the whole talk start-to-finish. Section 2 (the step-by-step tokenization → vectors → prediction build) is the most sequence-dependent section and the most worth rehearsing individually.

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
A parameter is one of the individual numerical values inside a neural network — the "weights" mentioned above — that gets adjusted during training. Think of each parameter as a small dial the model learns to turn to just the right setting so it produces good outputs. When you hear a model "has 70 billion parameters," that means it has 70 billion of these tunable dials. More parameters generally give a model more capacity to capture complex patterns — which is part of why bigger models can be more capable, but also why they need so much more memory to run (see "Why do bigger models need bigger hardware?" below).
> Analogy: like a massive soundboard with billions of tiny sliders, each nudged to a precise position during training so that, combined, they produce the right output for a given input.

**Q: Why do bigger models need bigger hardware?**
A model's "parameters" are roughly the number of knobs it learned to tune during training — more parameters generally means more capability, but also means the model takes up more memory. The jump is stark even within one model family: Google's small edge model Gemma e2b needs about 3GB of memory, while its own flagship Gemma model (31 billion parameters) needs around 17-18GB. Go out to the true frontier and the numbers jump again — a 70-billion-parameter model needs around 40GB to run well (that figure assumes a compressed/"quantized" version; a full-precision 70B model would need closer to 140GB), more than any consumer graphics card has on its own (high-end consumer GPUs typically top out around 32GB, e.g. the RTX 5090). The very largest open models released in 2026 — like Kimi K2.6 or DeepSeek's largest models — have around 700 billion to 1 trillion parameters, requiring hundreds of gigabytes of memory spread across multiple enterprise-grade GPUs: roughly the same as lining up the graphics cards from 15-20 top-of-the-line gaming PCs, networked together, just to hold one model in memory before it's answered a single question.
> The "aha": it's not that ChatGPT, Claude, or Gemini's best models are secretly special code — they're often just too large to fit on a personal computer, so the company runs them in a data center and lets you access them over the internet instead. ("Quantization" is the technique that shrinks a model's memory footprint, like compressing a photo, at a small cost to quality — it's how larger models get squeezed onto consumer hardware at all.)

**Q: What is an agent?**
A regular chatbot just talks — it responds with text, but can't *do* anything beyond that. An "agent" extends an LLM by giving it tools: the ability to search the web, run code, browse a website, or call other software. It works in a loop — take an action, look at the result, decide the next step, repeat — continuing until it reaches its goal or hits a stopping point (like a step limit). "Autonomous" sounds more dramatic than it usually is in practice: agents can only do what their given tools allow, and most real-world uses still include guardrails or a human checking in before anything important happens.
> Analogy: think of a regular chatbot as a knowledgeable person answering questions over the phone — they can tell you what to do, but can't do it themselves. An agent is like handing that same person a set of keys and letting them actually go complete the task, checking back in with you as they go.

**Q: Does the model actually *understand* what it's saying, or is it just predicting symbols?**
This is genuinely debated, and there's a famous framing for it: philosopher John Searle's **Chinese Room argument** (1980). Imagine a person locked in a room who doesn't speak Chinese, but has a giant rulebook that tells them exactly which Chinese symbols to write back out in response to any Chinese symbols slipped under the door. From outside, the room appears fluent in Chinese — but the person inside is just matching patterns against a rulebook, with zero understanding of what any of it means. Searle's point: following rules to manipulate symbols isn't the same thing as genuinely understanding them.
> Why it's relevant here: an LLM predicting the next token from learned statistical patterns is arguably doing something structurally similar — extraordinarily sophisticated pattern-matching, not necessarily "understanding" in the human sense. Whether that distinction is real, or even meaningful, is an open philosophical debate — not a settled fact. It's a good note of intellectual humility to land on if the conversation goes there.

**Q: How does image generation work?**
Briefly: it's a different technology from LLMs. Most image generators start with a canvas of random visual "noise" and gradually clean it up, step by step, into a coherent picture that matches your text description — a process called diffusion. (Kept short on purpose — happy to expand this into its own section if you ever want to cover it in a future talk.)

**Q: What is contained in an LLM model file?**
A model file bundles everything needed to run the model: the weights (the billions of learned parameter values — the bulk of the file size), metadata describing the architecture (how many layers, attention heads, etc.), and the tokenizer/vocabulary for converting text to tokens and back. Ollama's format (GGUF) packages all of this into a single self-contained file — that's literally what gets downloaded when you run ollama pull.

> Analogy: like a shipped IKEA box that contains the parts (weights), the assembly instructions (architecture metadata), and the glossary of part names (tokenizer) all in one package, instead of needing three separate boxes.