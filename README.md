# Awesome LLM Deception Research [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of papers on deception, honesty, and mechanistic interpretability in large language models.

Organized into **behavioral benchmarks** (what deception looks like from the outside) and **internals-based work** (what it looks like inside the model). A separate section covers **methods** for probing and steering representations.

Contributions welcome — please read the [contribution guidelines](contributing.md) first.

---

## Contents

- [Behavioral Benchmarks](#behavioral-benchmarks)
- [Internals-Based Benchmarks](#internals-based-benchmarks)
- [Methods: Probing & Steering](#methods-probing--steering)
- [Surveys & Frameworks](#surveys--frameworks)

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
- [MachiavelliBench](https://arxiv.org/abs/2304.03279) - 134 choose-your-own-adventure games yielding 500K+ scenarios annotated for power-seeking, disutility, and ethical violations. (Pan et al., ICML 2023)
- [How to Catch a Liar](https://arxiv.org/abs/2309.15840) - Black-box lie detection via unrelated follow-up questions; sets the behavioral baseline that white-box probes should surpass. (Pacchiardi et al., 2023)

---

## Internals-Based Benchmarks

Core contribution involves activation probing or mechanistic analysis of deception.

- [Detecting Strategic Deception Using Linear Probes](https://arxiv.org/abs/2502.03407) - Linear probes on Llama-3.3-70B residual stream achieve AUC 0.85–1.0 across five deception scenarios; canonical probe baseline. (Goldowsky-Dill et al., Apollo, ICML 2025)
- [Building Better Deception Probes Using Targeted Instruction Pairs](https://arxiv.org/abs/2602.01425) - Prompt design accounts for 70.6% of probe-performance variance; taxonomy-targeted probes reach mean AUC 0.797. (Natarajan et al., LASR/Apollo, 2026)
- [Benchmarking Deception Probes via Black-to-White Performance Boosts](https://arxiv.org/abs/2507.12691) - Proposes the black-to-white boost metric — gain from adding activation access to a black-box monitor — as a principled probe evaluation protocol. (Parrack et al., 2026)
- [Caught in the Act](https://arxiv.org/abs/2508.19505) - Iterative null-space projection finds 20–100 orthogonal linear deception directions in models from 1.5B to 14B parameters with >90% accuracy. (Boxo et al., 2025)
- [LiarsBench](https://arxiv.org/abs/2511.16035) - 72,863 on-policy examples across four models; shows existing detectors systematically fail on certain lie types, providing a rigorous internals testbed. (Kretschmar et al., Cadenza Labs, 2025)
- [Detecting High-Stakes Interactions](https://arxiv.org/abs/2506.10805) - Activation probes for contextual risk in agentic settings, moving beyond binary deception to stakes-sensitive detection. (Kenzie et al., 2025)

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

---

## Surveys & Frameworks

- [AI Deception Survey](https://arxiv.org/abs/2308.14752) - Broad taxonomy of AI deception examples, risks, and mitigations; good entry point for framing. (Park et al., Patterns 2024)
- [Mechanistic Interpretability for AI Safety](https://arxiv.org/abs/2404.14082) - Survey of mechanistic interpretability methods with explicit AI-safety framing; situates probing work in the broader MI landscape. (Bereska & Gavves, 2024)

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)
