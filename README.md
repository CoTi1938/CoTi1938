# Hi, I'm CoTi1938 👋

I work on CUDA and Metal inference in colibri, Vincenzo Fornaro’s open-source C engine for mixture-of-experts models. **65 of my pull requests have been merged upstream**. The first 45 were in `main` by v2.2.0, and the next 20 were integrated into `dev` in a single CUDA batch. [colibri](https://github.com/JustVugg/colibri) · [All merged PRs](https://github.com/JustVugg/colibri/pulls?q=is%3Apr+author%3ACoTi1938+is%3Amerged) · [v2.2.0](https://github.com/JustVugg/colibri/pull/2965) · [CUDA integration](https://github.com/JustVugg/colibri/pull/3064)

## CUDA on eight NVIDIA GPUs

<a name="results-by-gpu"></a>
<a name="cuda-pull-requests-in-order"></a>

I measured Qwen3.6-35B-A3B INT4 on eight NVIDIA GPUs, from the L4 and RTX 3090 to the A100 and RTX PRO 6000. Each card ran 16 workloads spanning fixed prompts and an eight-turn chat. **Prompt processing improved in all 128 GPU/workload combinations, and steady generation improved in 127.** The optimized build matched the baseline’s full FP32 logits bit for bit in all 384 paired comparisons. [Timings and correctness by GPU](https://github.com/CoTi1938/colibri/tree/vetrina#results-by-gpu) · [The 20 PRs in order](https://github.com/CoTi1938/colibri/tree/vetrina#cuda-pull-requests-in-order)

On an **RTX 4090 rented on Vast.ai**, a 16,384-token prompt went from **6,295 to 12,311 tokens/s**. Steady generation went from 162.51 to 180.89 tokens/s. In a separate test on the maintainer’s RTX PRO 4000 Blackwell SFF Edition, a 9,870-token prompt went from 3.3 to 2.4 seconds with the same generated text. [4090 timings](https://github.com/JustVugg/colibri/blob/e8b1c9b3f28c4724603e64a3a692f2e9d1141344/docs/experiments/qwen36-cuda-17-rtx-4090-2026-11-22/base.md) · [4090 logit comparison](https://github.com/JustVugg/colibri/blob/e8b1c9b3f28c4724603e64a3a692f2e9d1141344/docs/experiments/qwen36-cuda-17-rtx-4090-2026-11-22/correctness.txt) · [Maintainer’s test](https://github.com/JustVugg/colibri/pull/3064)

## The first Metal graph

I built colibri’s Metal inference graph for Qwen3.6. On a fanless **8 GB MacBook Air M1**, the 35B model read a 512-token prompt at **111 tokens/s on Metal**, up from **3.13 on CPU**. On a separate test using the same 1,024 continuation tokens, mean negative log-likelihood was 2.945 on Metal and 2.948 on CPU. [Merged graph PR](https://github.com/JustVugg/colibri/pull/2298) · [Four-run timings](https://github.com/JustVugg/colibri/blob/e479104ae01bdc40ce81e675299b1d230891b321/docs/experiments/qwen36-metal-graph-2026-10-05/summary.txt) · [Same-text quality check](https://github.com/JustVugg/colibri/blob/e479104ae01bdc40ce81e675299b1d230891b321/docs/experiments/qwen36-metal-graph-2026-10-05/quality.txt)

<a name="more-work-in-upstream-main"></a>

[More upstream work on CUDA, Vulkan, GGUF and container memory](https://github.com/CoTi1938/colibri/tree/vetrina#more-work-in-upstream-main) · [formine_nadir.7q@icloud.com](mailto:formine_nadir.7q@icloud.com)
