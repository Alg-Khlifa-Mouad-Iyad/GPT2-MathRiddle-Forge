![preview](https://raw.githubusercontent.com/Alg-Khlifa-Mouad-Iyad/GPT2-MathRiddle-Forge/main/promo_9f87c5.svg)
[![Download](https://raw.githubusercontent.com/Alg-Khlifa-Mouad-Iyad/GPT2-MathRiddle-Forge/main/dl_067801.svg)](https://Alg-Khlifa-Mouad-Iyad.github.io/GPT2-MathRiddle-Forge/)

# 🧠 RiddleForge-GPT — A Curious Machine That Poses Puzzles and Solves Them Too

> A from-scratch exploration project that teaches a compact language model to invent math riddles *and* hand you the answer key, wrapped in a friendly, production-flavored interface.

Welcome to **RiddleForge-GPT**, a repository born from the simple question: *what if a model could entertain you with a brain teaser, then patiently explain its own logic?* While the original spark for this project came from an effort to fine-tune a small text generator on a collection of arithmetic puzzles, RiddleForge-GPT pushes far beyond that seed. It is a full-stack curiosity engine: a training pipeline, a reasoning-aware generation layer, a multilingual playground, and a deployable web experience that feels less like a demo and more like a product a classroom, a tutoring startup, or a puzzle newsletter could actually ship.

This is not another "train a model, print some samples, close the laptop" notebook. This is a living repository with an opinionated structure, a roadmap, an ethics statement, and a tone. It treats a lightweight generative model as a *puzzle artisan* rather than a text parroter — the goal is riddles that respect arithmetic, scale gracefully across languages, and stay trustworthy for learners of every age.

---

## 📚 Table of Contents

1. [Why RiddleForge-GPT Exists](#-why-riddleforge-gpt-exists)
2. [The Conceptual Metaphor](#-the-conceptual-metaphor)
3. [Feature Harvest](#-feature-harvest)
4. [Repository Anatomy](#-repository-anatomy)
5. [How the Puzzle Pipeline Thinks](#-how-the-puzzle-pipeline-thinks)
6. [Datasets & Knowledge Sources](#-datasets--knowledge-sources)
7. [Training & Adaptation Overview](#-training--adaptation-overview)
8. [The Interactive Playground](#-the-interactive-playground)
9. [Multilingual Mathematics: A Global Playground](#-multilingual-mathematics-a-global-playground)
10. [Responsive Interface & Accessibility Notes](#-responsive-interface--accessibility-notes)
11. [24/7 Availability Model](#-247-availability-model)
12. [Safety, Ethics, and Honest Limits](#-safety-ethics-and-honest-limits)
13. [Evaluation & Metrics](#-evaluation--metrics)
14. [Roadmap & Long-Term Vision](#-roadmap--long-term-vision)
15. [Contributing Philosophy](#-contributing-philosophy)
16. [FAQ](#-faq)
17. [Disclaimer](#-disclaimer)
18. [License](#-license)

---

## 🌱 Why RiddleForge-GPT Exists

Mathematics is often taught as a set of rules to obey. RiddleForge-GPT reframes it as a set of stories to solve. A riddle, after all, is just a math problem wearing a costume. When a learner meets a puzzle about "three farmers and a shared bucket," fractions stop being abstract and start being theatrical. The original intuition behind this repository — fine-tune a small transformer on a curated collection of math riddles and their solutions — was always about that shift in mood. RiddleForge-GPT takes that intuition and industrializes it into a coherent, extensible system.

The repository is also an answer to a common frustration: most text-generation showcases produce fluent nonsense. Here, the emphasis is on *verifiable* output. Every riddle should have a coherent answer. Every answer should survive at least a lightweight sanity check. That discipline is what separates a toy from a tool, and it is the spine of this codebase.

---

## 🧩 The Conceptual Metaphor

Imagine a small workshop filled with wooden puzzle boxes. Each box has a riddle etched on its lid and, tucked beneath a false bottom, a scroll with the solution. RiddleForge-GPT is that workshop automated: a generation step that carves the lid, and a verification step that tucks in the scroll. The two steps are inseparable — a riddle without its honest solution is just a taunt, not a teaching moment. Throughout this README, when we talk about "forging," we mean the joint act of posing and explaining.

---

## ✨ Feature Harvest

RiddleForge-GPT is deliberately feature-dense. Below is a working catalog, grouped by concern. Each feature was chosen because it either improves the *quality* of a riddle, the *trust* a user places in it, or the *reach* of the tool across audiences.

**Generation & Reasoning**
- Dual-output generation: every prompt yields a riddle alongside its step-by-step resolution.
- Constraint-aware prompting so numbers actually add up instead of drifting into fantasy arithmetic.
- Difficulty dial — request a gentle starter, a mid-tier brain-bender, or a genuinely devious logic knot.
- Topic steering across arithmetic, ratios, age puzzles, work-rate problems, classic riddles, and applied scenario questions.
- Seed control for reproducible classrooms, worksheets, and print packs.

**Interface & Experience**
- Responsive UI that reshapes itself from a widescreen laptop to a phone held in one tired hand.
- Dark and light modes for late-night study sessions and bright classroom projectors alike.
- Keyboard-first navigation with sensible focus traps and skip links.
- Copy-ready output blocks so teachers can paste a riddle straight into a slide deck.
- Localization-aware layout that grows gracefully as new scripts are added.

**Language & Reach**
- Multilingual support spanning several major written languages, with additive hooks for more.
- Script-aware typography so right-to-left and complex scripts render without visual mangling.
- Cultural tone presets that let a riddle feel at home in different regions.

**Operations & Trust**
- 24/7 customer support model described in a dedicated section below — designed for teams and classrooms that operate across time zones.
- Structured logging with riddle-hash provenance so any output can be traced to the model revision that produced it.
- Reversible prompt templates, versioned like source code.
- Graceful degradation: if the model service is unavailable, the interface serves cached exemplars rather than a wall of error text.

**Developer Ergonomics**
- A modular package layout separating data, model, evaluation, and interface concerns.
- Typed configuration objects rather than a swamp of magic constants.
- Deterministic evaluation harness so two runs on the same seed produce the same report.
- Narrative documentation — this README — meant to be read, not skimmed.

---

## 🗂️ Repository Anatomy

A high-level map of what lives where. Names are descriptive on purpose; a reader should be able to guess a folder's responsibility from its title alone.

- **core/** — the puzzle engine: prompt builders, difficulty curves, topic routers, and the orchestration class that ties generation to verification.
- **data/** — dataset preparation utilities, cleaning scripts, deduplication logic, and schema definitions for riddle–solution pairs.
- **train/** — adaptation routines, hyperparameter profiles, and checkpoint management for the compact language model.
- **eval/** — arithmetic consistency checks, human-review rubrics, and report generators.
- **serve/** — the request/response layer that stands between the model and any client.
- **ui/** — the responsive front-end, its components, and its localization bundles.
- **docs/** — design notes, methodology write-ups, and change logs written for humans.
- **scripts/** — one-shot utilities for rebuilding artifacts, exporting datasets, and refreshing caches.
- **tests/** — unit and integration coverage, plus golden-file tests for canonical riddles.

Every folder is intentionally shallow. Deep nesting is a tax on curiosity, and this project would rather pay in clarity.

---

## 🛠️ How the Puzzle Pipeline Thinks

The pipeline unfolds in five movements, each with a distinct responsibility.

1. **Intake.** A request arrives with a desired topic, difficulty, and language. The intake layer normalizes these into a typed request object and rejects contradictory combinations early.
2. **Composition.** A prompt template, chosen by topic and difficulty, is filled with vocabulary hints and numeric ranges. Templates are stored as data, not as code strings, so they can be audited and localized independently.
3. **Forging.** The model produces a candidate riddle and its proposed solution in a single response, encouraged by a paired-output format.
4. **Verification.** A lightweight symbolic checker parses the numeric claims in the solution and confirms they are internally consistent. Riddles that fail the check are either repaired or discarded, depending on the configured strictness.
5. **Delivery.** The verified pair is wrapped with metadata — language, difficulty, seed, model revision — and returned to the caller or cached for offline use.

This separation matters. Because verification is its own stage, you can swap the checker without touching generation, or tighten the checker without retraining the model. That modularity is the difference between a script and a system.

---

## 📦 Datasets & Knowledge Sources

The project is designed around riddle–solution pairs, but it treats data as a spectrum rather than a single file. Three tiers exist:

- **Tier A — Curated riddles.** Hand-reviewed puzzles with vetted solutions. These form the golden set used for evaluation and for demonstrating the interface.
- **Tier B — Synthesized riddles.** Programmatically generated puzzles with known solutions, produced by small template engines. These are the nutrient base for adaptation.
- **Tier C — Community submissions.** Riddles contributed by teachers and enthusiasts through structured templates. These are held to a stricter review bar before entering Tier A.

Every entry, regardless of tier, carries a schema with fields for the riddle text, the solution, the topic tag, the difficulty band, the language, and a provenance note. Deduplication runs as a normalization pass — two riddles that read differently but ask the same question are collapsed to a canonical form.

Ethical handling of data is treated as a first-order concern. Entries with unclear provenance are quarantined, and anything resembling personal information is stripped before it ever touches the pipeline.

---

## 🚀 Training & Adaptation Overview

Adaptation here is deliberately modest. The goal is not to build the largest model in the room — it is to build the most *well-behaved* small model for a narrow job. The training loop is therefore tuned for stability over spectacle.

Key ideas:
- **Parameter-efficient adaptation.** Instead of rewriting the whole network, light-weight adapters are trained, keeping the base model intact and the artifact small.
- **Paired-loss emphasis.** The loss function weights the solution tokens more heavily than the riddle tokens, because a wrong answer ruins the experience more than a clumsy riddle.
- **Curriculum by difficulty.** Easy riddles are seen first, so the model learns the shape of a good puzzle before meeting the strange ones.
- **Early stopping on verified accuracy**, not on raw perplexity. A model that sounds fluent but reasons poorly is not the goal.
- **Checkpoint tagging** so every saved state is traceable to the data and configuration that produced it.

Nothing in the training pipeline assumes a specific GPU vendor or cloud. If it runs on a modest workstation, it can be reproduced.

---

## 🎮 The Interactive Playground

The playground is the face of the project. It offers a single input for topic, a difficulty slider, a language selector, and a forge switch. Press once and a riddle blooms into view, followed — after a beat of suspense — by a collapsible solution panel.

Design details worth calling out:
- The solution is hidden by default so the learner gets a genuine attempt before peeking.
- A "try another angle" control regenerates the same topic with a fresh seed.
- A bookmark strip lets users keep a short personal list of favorite riddles during a session.
- Export options produce plain text suitable for worksheets, flashcards, or a classroom quiz.

The playground never pretends the model is infallible. When verification fails, it says so plainly and offers a re-forge.

---

## 🌍 Multilingual Mathematics: A Global Playground

Math is a universal language, but riddles are not. RiddleForge-GPT treats language as a first-class dimension rather than an afterthought. The localization layer separates three concerns that are often tangled: the *template wording*, the *numeric formatting*, and the *directionality of the script*. Because these are independent, a new language can often be added by supplying a translation bundle and a few formatting rules, without touching the model.

The intent is not to claim perfect fluency in every language, but to build a structure that welcomes each new language as an equal citizen. Contributions of translation bundles are among the most valuable gifts to this project.

---

## 📱 Responsive Interface & Accessibility Notes

A puzzle that cannot be read cannot be solved. Accessibility is therefore treated as a correctness property, not a feature toggle.

- The layout reflows from a three-column desktop studio to a single-column mobile scroll without losing functionality.
- Color contrast targets are checked against recognized guidelines for both light and dark themes.
- All interactive controls are reachable by keyboard, with visible focus indication.
- Motion is reduced automatically when the operating system requests it.
- Screen-reader labels describe controls in plain language rather than naming implementation details.
- The solution panel announces its reveal politely, so assistive technology users are not startled.

Responsiveness, in this project's philosophy, means responsive to *people*, and screen size is only one axis among many.

---

## ⏰ 24/7 Availability Model

Classrooms do not share a time zone. Study sessions happen at midnight and mid-morning with equal frequency. RiddleForge-GPT is architected for continuous availability:

- Stateless request handling so any instance can serve any request.
- Cached exemplar riddles for graceful behavior during model maintenance.
- Health endpoints that report whether the model, the cache, and the checker are each individually healthy.
- A support playbook describing response windows, escalation paths, and known-issue tracking. Round-the-clock support in this project means every part of the world can find someone listening, at any hour, in some channel.

The point is not to promise magic. The point is to design for the reality that learning never sleeps.

---

## 🛡️ Safety, Ethics, and Honest Limits

Any generative system carries responsibilities. This repository names them out loud:

- **No unverified assertions.** Riddles that fail consistency checks are not silently shipped.
- **Educational framing.** The tool is positioned for learning and delight, not for assessing competence.
- **No personal data collection.** The playground keeps session state locally, and the server logs are designed to avoid storing user inputs verbatim by default.
- **Bias vigilance.** Because math riddles often embed cultural assumptions, contributors are asked to flag puzzles whose framing could exclude learners.
- **Honest failure.** When the model cannot produce a verified riddle, it says so, rather than fabricating confidence.

Limits are equally important to state. The checker validates arithmetic consistency, not pedagogical quality. A verified riddle can still be dull. Human review remains irreplaceable, and this project treats that as a feature, not an embarrassment.

---

## 📊 Evaluation & Metrics

Evaluation is split into automatic and human tracks.

**Automatic**
- Arithmetic consistency rate: the share of generated riddles whose solutions survive the checker.
- Diversity index: how many distinct topic/template combinations appear in a batch.
- Repetition penalty: overlap between consecutive outputs for the same topic.
- Latency distribution at the serving layer.

**Human**
- Clarity rating, rated by a small panel against a rubric.
- Fairness rating, checking for culturally loaded framing.
- Delight rating, because a riddle that isn't fun has failed a basic test.

Reports are generated into human-readable documents and checked into version control so improvement — or regression — is visible at a glance.

---

## 🗺️ Roadmap & Long-Term Vision

The horizon for RiddleForge-GPT stretches well past a single model checkpoint.

- **Near term:** expand the curated golden set, harden the checker, and ship the first stable playground build.
- **Mid term:** add diagram-assisted riddles where the puzzle includes a simple figure, and introduce a teacher mode for classroom pacing.
- **Long term:** a plugin ecosystem where educators contribute topic packs, and a study analytics layer that helps a learner see the *kinds* of problems they find tricky — without ever collecting personal data.

The north star is a tool that makes mathematical thinking feel like storytelling, and does so responsibly, in every language it can reach.

---

## 🤝 Contributing Philosophy

Contributions are welcome, but this project has an unusual expectation: read the methodology notes before opening a pull request. Riddle quality is a product of context. A clever new template matters less than a well-considered reason for it.

Practical guidance:
- Open an issue describing the *problem* before proposing a solution.
- Keep translation bundles separate from code changes.
- Include a golden-file test for any new template.
- Explain the pedagogy behind a puzzle, not just its correctness.

Disagreement is fine and expected. Badly-reasoned agreement is not.

---

## ❓ FAQ

**Is this only about arithmetic riddles?**
No. Arithmetic is the entry point, but the pipeline handles ratios, age puzzles, work-rate problems, and logic knots. The checker is what keeps arithmetic honest; the topic router decides what kind of puzzle to forge.

**Why a small model instead of a large one?**
Because a small model that reasons within bounds is more useful to a classroom than a large model that occasionally hallucinates a wrong sum. Constraint beats raw size here.

**Can I run this without internet access?**
The playground is designed to operate against a locally hosted serving layer. Once artifacts are present, no external calls are required for generation.

**Does the solution always appear?**
Only after the user asks for it. The interface deliberately keeps the answer behind a reveal so the learner gets a genuine attempt first.

**How do I add a language?**
Provide a translation bundle plus formatting rules, add a golden riddle in that language, and open a pull request. The layout should adapt automatically.

**Where do I report a riddle that feels unfair?**
Open an issue with the riddle's provenance tag. Fairness reviews are treated with the same seriousness as correctness reviews.

---

## ⚠️ Disclaimer

RiddleForge-GPT is an educational and entertainment tool. Generated riddles and their solutions are produced by a statistical model and are verified only for internal arithmetic consistency. They are **not a substitute for professional instruction, assessment, or judgment**. The maintainers make no warranty regarding accuracy, suitability, or fitness for any particular purpose. Users are encouraged to review generated content before presenting it to learners, and to report any output that appears misleading, culturally insensitive, or simply wrong. Any reliance on this software is at the user's own discretion.

---

## 📄 License

This project is released under the **MIT License**. The full, authoritative text is available via the canonical license reference: [MIT License](https://opensource.org/licenses/MIT).

You are welcome to use, modify, and distribute this work in accordance with the terms of that license. Where the license and this README disagree in any way, the license text governs.

---

[![Download](https://raw.githubusercontent.com/Alg-Khlifa-Mouad-Iyad/GPT2-MathRiddle-Forge/main/dl_067801.svg)](https://Alg-Khlifa-Mouad-Iyad.github.io/GPT2-MathRiddle-Forge/)