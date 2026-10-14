# Hanyu Yang

Research on the empirical and numerical behaviour of AI systems, alongside certified computer-assisted mathematical proofs. Every result is backed by public code, data, a reproduction command, and a persistent DOI on [Zenodo](https://zenodo.org/) or preprint on [alphaXiv](https://www.alphaxiv.org/).

**Portfolio & Landing Pages:** [severinvisionary.github.io](https://severinvisionary.github.io/) · **ORCID:** [0009-0005-0419-4070](https://orcid.org/0009-0005-0419-4070) · **Contact:** [hanyu.yang.92@gmail.com](mailto:hanyu.yang.92@gmail.com)

---

## Ranked Research Highlights

### 1. Multilingual Speculative Decoding: "No Refund for the Token Tax"
**[[Paper on alphaXiv](https://www.alphaxiv.org/abs/2610.speculative-decoding-token-tax-languagesv2)]** · **[[Zenodo DOI 10.5281/zenodo.23355847](https://doi.org/10.5281/zenodo.23355847)]** · **[[Code & Data](https://github.com/SeverinVisionary/fert-refund)]**
Across 21 languages on 200 FLORES-200 sentences, evaluated with Qwen3.5-9B (MTP head) and Gemma 4 E4B (assistant model), speculative acceptance length does *not* increase with tokenizer fertility. Every non-English language achieves a lower acceptance length than English. A six-language follow-up on vLLM confirms smaller real-world serving speedups than English, showing speculative decoding does not offset the multilingual tokenization penalty.

### 2. Whole-Document Batching & Gradient Noise: `doc-batch-gradients`
**[[Illustrated Post](https://severinvisionary.github.io/doc-batch-gradients/)]** · **[[Paper on alphaXiv](https://www.alphaxiv.org/abs/2610.long-documents-make-a-training-batch-smaller-than-it-looks)]** · **[[Zenodo DOI 10.5281/zenodo.23268861](https://doi.org/10.5281/zenodo.23268861)]** · **[[Code & Data](https://github.com/SeverinVisionary/doc-batch-gradients)]**
A preregistered empirical measurement using 512-token chunks on Pythia and OLMo-2 checkpoints demonstrating that within-document gradient correlation extends out to 16K tokens. For equal total tokens, whole-document 16K batches yield 3.5–4.9× fewer effective independent samples than packed web text on code repositories and ~2.3× fewer on arXiv (with books behaving close to packed controls).

### 3. Post-Training Catastrophic Forgetting vs. Vocabulary Prior Shift
**[[Paper on alphaXiv](https://www.alphaxiv.org/abs/2610.language-model-forgetting-vocabulary-bias)]** · **[[Zenodo DOI 10.5281/zenodo.23312067](https://doi.org/10.5281/zenodo.23312067)]** · **[[Code](https://github.com/SeverinVisionary/prior-shift-diagnostic)]** · **[[Data on Hugging Face](https://huggingface.co/datasets/coldrainy/prior-shift-diagnostic)]**
Tested across 14 released base/derived model pairs (OLMo-2, Qwen2.5, SmolLM2; 1B–7B). A context-free token bias recovers at most 9.8% of the web-text loss increase out-of-sample (bias plus temperature up to 36% in overconfident preference-tuned models). Under math continued pretraining, loss increases by up to 0.8 nats/token while context-free correction recovers at most 3.1%, confirming that forgetting is representational rather than a marginal vocabulary shift.

### 4. Numerical Precision & Rounding Error in FlashAttention
**[[Illustrated Post](https://severinvisionary.github.io/flashattention-rounding-error/)]** · **[[Paper on alphaXiv](https://www.alphaxiv.org/abs/2610.flashattention-rounding-error-analysis)]** · **[[Zenodo DOI 10.5281/zenodo.23179058](https://doi.org/10.5281/zenodo.23179058)]**
Forward rounding-error analysis of FlashAttention-2 vs. standard two-pass attention. While both share the same worst-case error bound, FlashAttention-2 achieves higher precision on peaked attention distributions. However, because split-KV reduction does not renormalize, outputs that should equal 1 deviate by up to 2.2% on an NVIDIA L4 as logits grow. Also constructs counterexamples disproving published $O(u \log n)$ error bounds.

### 5. Explicit Terraces for All Non-Abelian Groups of Order 256 and 384
**[[Zenodo DOI 10.5281/zenodo.22785373](https://doi.org/10.5281/zenodo.22785373)]** · **[[Repository](https://github.com/SeverinVisionary/bailey-terraces-256-384)]**
Constructed explicit terraces for all 56,070 non-abelian groups of order 256 and all 20,154 of order 384 across 76,325 witness records, resolving the two remaining open orders in Theorem 32(vi) of Ollis's dynamic survey DS10 (*Sequenceable Groups and Related Topics*). This establishes that every non-abelian group of order $\le 511$ possesses a terrace. Verified via standalone Python verifier and GAP Small Groups checks.

### 6. Lean 4 Formal Verification: Twofold Hamming Covering $K(8,1,2) \ge 61$
**[[Zenodo DOI 10.5281/zenodo.22217672](https://doi.org/10.5281/zenodo.22217672)]** · **[[Repository](https://github.com/SeverinVisionary/oeis-a004045)]** · **[[OEIS A004045](https://oeis.org/A004045)]**
A machine-checked Lean 4 formalization (zero `sorry`s) proving the lower bound $K(8,1,2) \ge 61$ for binary twofold covering codes (pinning down $61 \le K(8,1,2) \le 64$, the first unknown term of OEIS A004045), together with an elementary even-$n$ theorem improving five published bounds.

---

## AI Systems & Optimization Research

- **Sliding-Window Attention & Fake-Fact Pull:** Preregistered test in three matched 665M models (full attention, SWA-128, SWA-128 with NoPE global layers). Confusable fake facts show no discontinuity at the 128-token window boundary ($\Delta S = -0.054$), yet standard hybrid attention models select fake facts twice as often across all distances (71% vs. 35% at 96 tokens).  
  [[Paper](https://www.alphaxiv.org/abs/2610.sliding-window-hybrids-fake-facts)] · [[DOI 10.5281/zenodo.23311150](https://doi.org/10.5281/zenodo.23311150)]
- **Overfitting vs. Overconfidence at the Data Wall (`calrep`):** Across 125 public C4 checkpoints (7M–2.8B, 1–64 epochs), scalar temperature scaling eliminates ~32% of the empirical data-repetition penalty ($\rho = 0.682$ [0.580, 0.858]), demonstrating that overconfidence contributes substantially to the apparent data wall.  
  [[Paper](https://www.alphaxiv.org/abs/2610.overfitting-overconfidence-data-wall)] · [[DOI 10.5281/zenodo.23291816](https://doi.org/10.5281/zenodo.23291816)] · [[Code](https://github.com/SeverinVisionary/calrep)]
- **AdaGrad Under Heavy-Tailed Noise:** Resolves Liu's open question on the $p = 4/3$ heavy-tailed threshold. Proves the slowdown is driven by noise asymmetry: symmetric noise achieves $T^{-(p-1)/(2p)}$, while asymmetric noise with small damping is sharp at $(3p-4)/(4p)$. Damping smoothly recovers the symmetric rate.  
  [[Paper](https://www.alphaxiv.org/abs/2610.adagrad-heavy-tailed-noise-damping)] · [[DOI 10.5281/zenodo.23225828](https://doi.org/10.5281/zenodo.23225828)] · [[Illustrated Post](https://severinvisionary.github.io/adagrad-heavy-tailed-noise/)]
- **Byte-Pair Encoding (BPE) Worst-Case Bound:** Constructed an explicit family of strings showing BPE can lose more than half of optimal pair-encoding utility, lowering the upper bound from $5/8$ to $(1 - e^{-2})/2 \approx 0.4323$ (exact for token length $\le 3$).  
  [[Paper](https://www.alphaxiv.org/abs/2610.byte-pair-encoding-optimal-compression)] · [[DOI 10.5281/zenodo.23207123](https://doi.org/10.5281/zenodo.23207123)] · [[Illustrated Post](https://severinvisionary.github.io/bpe-beyond-half/)]
- **Audit of Vocabulary Scaling Laws:** Evaluated Tao et al. (2024): converting loss to bits-per-character shifts the 70B optimal vocabulary size from 212K to 106K–119K or 550K–764K depending on fit. Leave-one-size-out cross-validation at 1.13B misses optimal vocabulary by 8–40% compute-equivalent.  
  [[Paper](https://www.alphaxiv.org/abs/2610.vocabulary-scaling-law-metric)] · [[DOI 10.5281/zenodo.23205402](https://doi.org/10.5281/zenodo.23205402)] · [[Illustrated Post](https://severinvisionary.github.io/vocabulary-scaling-law-metric/)]
- **Slack ($\delta$) in Hallucination Lower Bounds:** Empirically measured the slack term $\delta$ in Kalai et al.'s hallucination lower bound on OLMo-2 corpus frequencies across 2,083 individuals (+0.028 for 7B base model), demonstrating sensitivity to token frequencies and vacuous bounds under uniform weighting.  
  [[Illustrated Post](https://severinvisionary.github.io/hallucination-bound-delta/)] · [[DOI 10.5281/zenodo.23225543](https://doi.org/10.5281/zenodo.23225543)]

---

## Certified Mathematics & Exact Computation

- **Alternating Plane Graphs:** Settled Conjectures 10.1 and 10.2 of Althöfer et al. (2015), and generated verified witnesses across 54 orders for Conjecture 10.3.  
  [[Repository](https://github.com/SeverinVisionary/alternating-plane-graphs)] · [[DOI 10.5281/zenodo.22269200](https://doi.org/10.5281/zenodo.22269200)]
- **Hypergraph Ramsey Number Lower Bounds:** Improved three entries of Radziszowski's *Small Ramsey Numbers* (§7.1(a)): $R(4,4,4;3) \ge 84$, $R(4,6;3) \ge 64$, and $R(5,5;4) \ge 36$ via group-invariant orbit colourings.  
  [[Repository](https://github.com/SeverinVisionary/hypergraph-ramsey-bounds)] · [[DOI 10.5281/zenodo.22698342](https://doi.org/10.5281/zenodo.22698342)]
- **Bernstein's Constant to 10 Certified Digits:** Rigorously proved $\beta = 0.2801694990$ using Arb interval arithmetic, doubling the precision of the 1985 Varga–Carpenter enclosure.  
  [[Repository](https://github.com/SeverinVisionary/bernstein-constant-certificate)] · [[DOI 10.5281/zenodo.22106774](https://doi.org/10.5281/zenodo.22106774)] · [[OEIS A073001](https://oeis.org/A073001)]
- **Heilbronn's Triangle Problem in the Disk:** Certified lower bound construction $\alpha_{\text{disk}}(14) \ge 0.0767158857...$ using an explicit 14-point configuration in exact integer coordinates (+1.075% over prior best).  
  [[Repository](https://github.com/SeverinVisionary/heilbronn-records)] · [[DOI 10.5281/zenodo.22091169](https://doi.org/10.5281/zenodo.22091169)]
