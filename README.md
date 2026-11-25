# Hi, I'm CoTi1938 👋

I write CUDA kernels for colibri and built its Qwen3.6 Metal graph for Apple Silicon. Colibri is Vincenzo Fornaro’s open-source C engine for mixture-of-experts models. [colibri](https://github.com/JustVugg/colibri) · [65 merged pull requests](https://github.com/JustVugg/colibri/pulls?q=is%3Apr+author%3ACoTi1938+is%3Amerged)

## CUDA on eight NVIDIA GPUs

<a name="results-by-gpu"></a>
<a name="cuda-pull-requests-in-order"></a>

I optimized colibri’s CUDA path for Qwen3.6-35B-A3B INT4 and tuned it for eight NVIDIA GPUs. Each card ran 16 workloads, including an eight-turn chat. **Prompt processing was faster in all 128 GPU–workload comparisons**, and steady generation was faster in 127. Across three runs per workload on each GPU, the optimized code produced the same FP32 logits as the baseline, bit for bit. [Timings and correctness by GPU](https://github.com/CoTi1938/colibri/tree/vetrina#results-by-gpu) · [The 20 PRs in order](https://github.com/CoTi1938/colibri/tree/vetrina#cuda-pull-requests-in-order)

On the **RTX 4090**, colibri processed a 16,384-token prompt at **12,311 tokens/s**, up from **6,295**. Steady generation rose from 162.51 to 180.89 tokens/s. In a separate test on an RTX PRO 4000 Blackwell SFF Edition, the maintainer saw a 9,870-token prompt go from 3.3 to 2.4 seconds with the same generated text. [4090 timings](https://github.com/JustVugg/colibri/blob/e8b1c9b3f28c4724603e64a3a692f2e9d1141344/docs/experiments/qwen36-cuda-17-rtx-4090-2026-11-22/base.md) · [4090 logit comparison](https://github.com/JustVugg/colibri/blob/e8b1c9b3f28c4724603e64a3a692f2e9d1141344/docs/experiments/qwen36-cuda-17-rtx-4090-2026-11-22/correctness.txt) · [Maintainer’s test](https://github.com/JustVugg/colibri/pull/3064)

<a name="the-first-metal-graph"></a>

## Qwen3.6 on Apple Silicon

On a fanless **MacBook Air M1 with 8 GB of unified memory**, my Metal graph ran the 35B model and processed a 512-token prompt at **111 tokens/s**, up from **3.13 tokens/s on CPU**. [Merged graph PR](https://github.com/JustVugg/colibri/pull/2298) · [Four-run timings](https://github.com/JustVugg/colibri/blob/e479104ae01bdc40ce81e675299b1d230891b321/docs/experiments/qwen36-metal-graph-2026-10-05/summary.txt) · [Same-text quality check](https://github.com/JustVugg/colibri/blob/e479104ae01bdc40ce81e675299b1d230891b321/docs/experiments/qwen36-metal-graph-2026-10-05/quality.txt)

<a name="more-work-in-upstream-main"></a>

[More upstream work on CUDA, Vulkan, GGUF and container memory](https://github.com/CoTi1938/colibri/tree/vetrina#more-work-in-upstream-main) · [formine_nadir.7q@icloud.com](mailto:formine_nadir.7q@icloud.com)
