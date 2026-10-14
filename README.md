# Hanyu Yang

Empirical and numerical research on large language models and AI systems — focusing on inference efficiency, scaling laws, training dynamics, and post-training mechanics.

🌐 **Portfolio:** [severinvisionary.github.io](https://severinvisionary.github.io/) · ✉️ **Contact:** [hanyu.yang.92@gmail.com](mailto:hanyu.yang.92@gmail.com) · 🆔 **ORCID:** [0009-0005-0419-4070](https://orcid.org/0009-0005-0419-4070)

---

## Top 5 AI Research Highlights

### 1. Speculative Decoding Across 21 Languages ("No Refund for the Token Tax")
- **The Question:** Does speculative decoding help non-English languages catch up by accepting more tokens per step to offset high tokenizer fertility?
- **Finding:** No. Across 21 languages on FLORES-200 (Qwen3.5-9B with MTP, Gemma 4 E4B with assistant), acceptance length does *not* rise with fertility — every non-English language has a lower acceptance length than English. Serving benchmarks in vLLM confirm that real-world speedups remain lower in non-English languages.
- **Links:** [Paper (alphaXiv)](https://www.alphaxiv.org/abs/2610.speculative-decoding-token-tax-languagesv2) · [Code & Data (GitHub)](https://github.com/SeverinVisionary/fert-refund) · [DOI 10.5281/zenodo.23355847](https://doi.org/10.5281/zenodo.23355847)

### 2. Whole-Document Batches Make Training Smaller Than It Looks (`doc-batch-gradients`)
- **The Question:** In long-context pretraining, does batching whole documents rather than packing random chunks dilute effective gradient signal?
- **Finding:** Yes. Within-document gradient correlation extends out to 16K tokens. For equal total tokens, whole-document 16K batches yield 3.5–4.9× fewer effective independent samples than packed web text on code repositories, and ~2.3× fewer on arXiv.
- **Links:** [Illustrated Post](https://severinvisionary.github.io/doc-batch-gradients/) · [Paper (alphaXiv)](https://www.alphaxiv.org/abs/2610.long-documents-make-a-training-batch-smaller-than-it-looks) · [Code & Data (GitHub)](https://github.com/SeverinVisionary/doc-batch-gradients) · [DOI 10.5281/zenodo.23268861](https://doi.org/10.5281/zenodo.23268861)

### 3. Is LLM Forgetting Just a Marginal Vocabulary Shift? (`prior-shift-diagnostic`)
- **The Question:** When language models undergo post-training (RLHF/DPO/SFT) or continued pretraining, is their loss increase on general text simply an uncalibrated shift in unigram token frequencies?
- **Finding:** No. Tested across 14 released model pairs (OLMo-2, Qwen2.5, SmolLM2; 1B–7B), an optimal context-free token bias recovers at most 9.8% of the web-text loss increase out of sample (and $\le 3.1\%$ under math continued pretraining). Forgetting is fundamentally representational, not a surface vocabulary reweighting.
- **Links:** [Paper (alphaXiv)](https://www.alphaxiv.org/abs/2610.language-model-forgetting-vocabulary-bias) · [Code (GitHub)](https://github.com/SeverinVisionary/prior-shift-diagnostic) · [Data (Hugging Face)](https://huggingface.co/datasets/coldrainy/prior-shift-diagnostic) · [DOI 10.5281/zenodo.23312067](https://doi.org/10.5281/zenodo.23312067)

### 4. FlashAttention-2 Rounding Error & Split-KV Scale Drift
- **The Question:** How does the forward floating-point accuracy of FlashAttention-2 compare to standard attention, and where does numerical error accumulate?
- **Finding:** FlashAttention-2 shares the same worst-case error bound as two-pass attention and is more accurate on peaked distributions. However, split-KV reduction omits renormalization, introducing scale drift up to 2.2% on an NVIDIA L4 as logits grow. The work also constructs counterexamples disproving previously published $O(u \log n)$ bounds.
- **Links:** [Illustrated Post](https://severinvisionary.github.io/flashattention-rounding-error/) · [Paper (alphaXiv)](https://www.alphaxiv.org/abs/2610.flashattention-rounding-error-analysis) · [DOI 10.5281/zenodo.23179058](https://doi.org/10.5281/zenodo.23179058)

### 5. Overfitting vs. Overconfidence at the Data Wall (`calrep`)
- **The Question:** When training language models on multi-epoch repeated data, how much of the performance penalty comes from uncalibrated overconfidence versus genuine memorization/overfitting?
- **Finding:** Across 125 public C4 checkpoints (7M–2.8B parameters, 1–64 epochs), cross-fitted scalar temperature scaling eliminates roughly one-third of the empirical data-repetition penalty ($\rho = 0.682$), showing that uncalibrated prediction confidence drives a substantial portion of the apparent "data wall."
- **Links:** [Paper (alphaXiv)](https://www.alphaxiv.org/abs/2610.overfitting-overconfidence-data-wall) · [Code & Data (GitHub)](https://github.com/SeverinVisionary/calrep) · [DOI 10.5281/zenodo.23291816](https://doi.org/10.5281/zenodo.23291816)
