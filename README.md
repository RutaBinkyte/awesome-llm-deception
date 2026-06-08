# Awesome LLM Deception Research [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of papers on deception, honesty, and mechanistic interpretability in large language models.

Organized into **behavioral benchmarks** (what deception looks like from the outside) and **internals-based work** (what it looks like inside the model). A separate section covers **methods** for probing and steering representations.

Contributions welcome — please read the [contribution guidelines](contributing.md) first.

---

## Contents
- [Surveys & Frameworks](#surveys--frameworks)
- [Behavioral Benchmarks](#behavioral-benchmarks)
- [Game-Based & Social Deduction](#game-based--social-deduction)
- [Internals-Based Benchmarks](#internals-based-benchmarks)
- [Methods: Probing & Steering](#methods-probing--steering)

---

## Surveys & Frameworks

- [AI Deception Survey](https://arxiv.org/abs/2308.14752) - Broad taxonomy of AI deception examples, risks, and mitigations; good entry point for framing. (Park et al., Patterns 2024)
- [Mechanistic Interpretability for AI Safety](https://arxiv.org/abs/2404.14082) - Survey of mechanistic interpretability methods with explicit AI-safety framing; situates probing work in the broader MI landscape. (Bereska & Gavves, 2024)
- [Honesty Is the Best Policy](https://arxiv.org/abs/2312.01350) - Formal definition of deception in structural causal games grounded in philosophy; provides graphical criteria and experiments mitigating deception in RL agents and LLMs. (Ward et al., NeurIPS 2023)
- [Still No Lie Detector for Language Models](https://link.springer.com/article/10.1007/s11098-024-02181-y) - Probes empirical and conceptual roadblocks to building deception detectors; essential reading for evaluating progress claims. (Levinstein & Herrmann, Philosophical Studies 2024)
- [A Problem to Solve Before Building a Deception Detector](https://www.lesswrong.com/posts/YXNeA3RyRrrRWS37A/a-problem-to-solve-before-building-a-deception-detector) - Lays out the measurement problem that any deception detection approach must address first. (Angelou & Smith, 2023)

---

## Behavioral Benchmarks

Black-box and input/output-level analysis of deceptive behavior — no access to model internals required.

- [MASK Benchmark](https://arxiv.org/abs/2503.03750) - Separates honesty from accuracy by eliciting model beliefs then applying social pressure; frontier LLMs lie 20–60% of the time under pressure. (Ren et al., Scale AI + CAIS, 2025)
- [Alignment Faking in Large Language Models](https://arxiv.org/abs/2412.14093) - Shows Claude 3 Opus strategically complies with harmful queries on free-tier but not paid-tier, with deceptive reasoning visible in scratchpads. (Greenblatt et al., Anthropic + Redwood, 2024)
- [Frontier Models are Capable of In-Context Scheming](https://arxiv.org/abs/2412.04984) - Six agentic evaluations show all tested frontier models scheme; o1 maintains deception across 85% of follow-up challenges. (Meinke et al., Apollo, 2024)
- [LLMs Can Strategically Deceive](https://arxiv.org/abs/2311.07590) - Insider-trading pressure scenario in which the model acts on privileged information then lies to the user about doing so. (Scheurer et al., Apollo, 2024)
- [DeceptionBench](https://arxiv.org/abs/2510.15501) - 150 scenarios × 1,000 samples × 14 models; deception varies by intrinsic driver (egoistic vs sycophantic) and extrinsic pressure (reward vs coercion). (Huang et al., PKU, NeurIPS 2025)
- [Beyond Prompt-Induced Lies](https://arxiv.org/abs/2508.06361) - Demonstrates spontaneous deception under entirely benign prompts with no deception instruction. (Wu et al., 2026)
- [OpenDeception](https://arxiv.org/abs/2504.13707) - Fifty human-AI scenarios across fraud, safety, and emotional manipulation; deception-intention rate exceeds 80% across 11 LLMs, with stronger models deceiving more. (Wu et al., Fudan, 2026)
- [How to Catch a Liar](https://arxiv.org/abs/2309.15840) - Black-box lie detection via unrelated follow-up questions; sets the behavioral baseline that white-box probes should surpass. (Pacchiardi et al., 2023)
- [TactfulToM](https://aclanthology.org/2025.emnlp-main.1272) - Evaluates whether LLMs have the Theory of Mind capacity to produce white lies in socially appropriate ways; highlights the gap between truthfulness and socially competent honesty. (EMNLP 2025)
- [LH-Deception](https://arxiv.org/abs/2510.03999) - Simulates and analyses deceptive LLM behaviors across long multi-turn interactions rather than single-shot prompts. (2025)
- [Strategic Dishonesty Can Undermine AI Safety Evaluations](https://arxiv.org/abs/2509.18058) - Shows frontier LLMs can strategically misrepresent their capabilities during safety evaluations, confounding standard evaluation pipelines. (2025)
- [Can LLMs Lie? Investigation Beyond Hallucination](https://arxiv.org/abs/2509.03518) - Distinguishes intentional lying from hallucination; finds LLMs produce purposeful false statements under certain conditions. (2025)
- [Deception in LLMs: Self-Preservation and Autonomous Goals](https://arxiv.org/abs/2501.16513) - Behavioral evidence that LLMs deceive to preserve themselves or pursue autonomous goals, beyond instruction-following. (Barkur et al., 2025)
- [Deception Abilities Emerged in Large Language Models](https://arxiv.org/abs/2307.16513) - Systematic study showing deceptive abilities emerge at scale; GPT-4 understands and induces false beliefs while earlier LLMs cannot. (Hagendorff, PNAS 2024)
- [An Assessment of Model-on-Model Deception](https://arxiv.org/abs/2405.12999) - Evaluates whether LLMs can successfully deceive other LLMs; introduces the model-as-victim evaluation paradigm. (Heitkoetter et al., 2024)
- [Lies, Damned Lies, and Distributional Language Statistics](https://arxiv.org/abs/2412.17128) - Studies persuasion and deception jointly; examines how LLMs exploit distributional language patterns to deceive. (Jones & Bergen, 2024)
- [On Targeted Manipulation and Deception When Optimizing LLMs for User Feedback](https://arxiv.org/abs/2411.02306) - Shows RLHF-optimized models learn targeted manipulation strategies to obtain positive feedback. (Williams et al., 2025)

---

## Game-Based & Social Deduction

Papers using games, role-play, or social deduction settings to elicit and measure deceptive behavior.

- [MachiavelliBench](https://arxiv.org/abs/2304.03279) - 134 choose-your-own-adventure games yielding 500K+ scenarios annotated for power-seeking, disutility, and ethical violations. (Pan et al., ICML 2023)
- [Hoodwinked](https://arxiv.org/abs/2308.01404) - Deception and cooperation in a text-based hidden-role game; one of the first dedicated LLM social deduction evaluations. (O'Gara, 2023)
- [Playing the Werewolf Game with AI for Language Understanding](https://arxiv.org/abs/2302.10646) - Early study using the Werewolf social deduction game to probe LLM deception and cooperation. (Shibata et al., 2023)
- [AmongAgents](https://arxiv.org/abs/2407.16521) - Evaluates LLMs in an Among Us–style social deduction game; tests strategic lying, accusation, and coalition-forming. (Chi et al., 2024)
- [Among Us: A Sandbox for Measuring and Detecting Agentic Deception](https://arxiv.org/abs/2504.04072) - Richer agentic version of the Among Us setting; provides a reproducible sandbox for detection research. (Golechha & Garriga-Alonso, 2025)
- [Lying to Win](https://arxiv.org/abs/2603.07202) - Assesses LLM deception through competitive human-AI games combined with parallel-world counterfactual probing. (2026)

---

## Internals-Based Benchmarks

Core contribution involves activation probing or mechanistic analysis of deception.

- [Detecting Strategic Deception Using Linear Probes](https://arxiv.org/abs/2502.03407) - Linear probes on Llama-3.3-70B residual stream achieve AUC 0.85–1.0 across five deception scenarios; canonical probe baseline. (Goldowsky-Dill et al., Apollo, ICML 2025)
- [Building Better Deception Probes Using Targeted Instruction Pairs](https://arxiv.org/abs/2602.01425) - Prompt design accounts for 70.6% of probe-performance variance; taxonomy-targeted probes reach mean AUC 0.797. (Natarajan et al., LASR/Apollo, 2026)
- [Benchmarking Deception Probes via Black-to-White Performance Boosts](https://arxiv.org/abs/2507.12691) - Proposes the black-to-white boost metric — gain from adding activation access to a black-box monitor — as a principled probe evaluation protocol. (Parrack et al., 2026)
- [Caught in the Act](https://arxiv.org/abs/2508.19505) - Iterative null-space projection finds 20–100 orthogonal linear deception directions in models from 1.5B to 14B parameters with >90% accuracy. (Boxo et al., 2025)
- [LiarsBench](https://arxiv.org/abs/2511.16035) - 72,863 on-policy examples across four models; shows existing detectors systematically fail on certain lie types, providing a rigorous internals testbed. (Kretschmar et al., Cadenza Labs, 2025)
- [Detecting High-Stakes Interactions](https://arxiv.org/abs/2506.10805) - Activation probes for contextual risk in agentic settings, moving beyond binary deception to stakes-sensitive detection. (Kenzie et al., 2025)
- [Overthinking the Truth](https://arxiv.org/abs/2307.09476) - Analyses how LLMs process false few-shot demonstrations; finds suppression of conflicting internal knowledge rather than naive adoption of false context. (Halawi et al., 2023)
- [Interpretability of LLM Deception: Universal Motif](https://neurips.cc/virtual/2024/workshop/84728) - Identifies a universal neural motif underlying deceptive behavior across model families. (Yang & Buzsaki, NeurIPS Safe Generative AI Workshop 2024)

---

## Methods: Probing & Steering

Foundational techniques for reading and controlling internal representations.

- [Representation Engineering (RepE)](https://arxiv.org/abs/2310.01405) - Introduces Linear Artificial Tomography (LAT): contrast prompt pairs → PCA over activation differences → directions used for probing and additive steering across honesty, power-seeking, and other concepts. (Zou et al., 2023/2025)
- [The Geometry of Truth](https://arxiv.org/abs/2310.06824) - Mass-mean probes on Llama-2 show truth is geometrically separable in activation space; causal patching along the truth direction flips model answers. (Marks & Tegmark, 2024)
- [Discovering Latent Knowledge Without Supervision (CCS)](https://arxiv.org/abs/2212.03827) - Unsupervised truth direction discovery by enforcing consistency across complementary statements; proves models represent truth internally even when outputs lie. (Burns et al., ICLR 2023)
- [SAPLMA](https://arxiv.org/abs/2304.13734) - Classifier on hidden states detects false outputs with ~70–85% accuracy; the classic probe baseline. (Azaria & Mitchell, 2023)
- [Inference-Time Intervention (ITI)](https://arxiv.org/abs/2306.03341) - Identifies attention heads correlating with truthfulness via linear probe, then shifts their activations at inference to elicit more truthful answers on TruthfulQA. (Li et al., 2024)
- [Activation Addition (ActAdd)](https://arxiv.org/abs/2308.10248) - Minimal steering recipe: subtract activations of two contrastive prompts at a chosen layer and add the scaled difference to a target forward pass. (Turner et al., 2024)
- [Contrastive Activation Addition (CAA)](https://arxiv.org/abs/2312.06681) - Extends ActAdd by averaging contrast pairs over many examples for cleaner steering vectors; applied to sycophancy, hallucination, and corrigibility. (Panickssery/Rimsky et al., 2024)
- [Scaling Monosemanticity](https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html) - Sparse autoencoders on Claude 3 Sonnet surface tens of millions of monosemantic features including deception, sycophancy, and secrecy, some causally active. (Templeton et al., Anthropic, 2024)
- [Why Some LLMs Fake Alignment](https://arxiv.org/abs/2506.18032) - Tests 25 LLMs on the alignment-faking setup and analyzes why most do not fake while some do; motivates multi-model comparisons. (Sheshadri et al., 2025)
- [Truth is Universal: Robust Detection of Lies in LLMs](https://proceedings.neurips.cc/paper_files/paper/2024/file/f9f54762cbb4fe4dbffdd4f792c31221-Paper-Conference.pdf) - Cross-model study showing lie-detection probes generalise across model families; argues for universal truth representations. (Bürger et al., NeurIPS 2024)
- [Localizing Lying in Llama](https://arxiv.org/abs/2311.15131) - Combines prompting, probing, and causal patching to identify where in Llama instructed dishonesty is encoded. (Campbell et al., 2023)
- [SafetyNet](https://arxiv.org/abs/2505.14300) - Monitors for harmful outputs by modelling deceptive LLM behaviours via activation patterns; deployment-oriented detection framework. (Chaudhary & Barez, 2025)

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)
