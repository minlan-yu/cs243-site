# Warmup Project: LLM Inference Serving with vLLM

This warm-up project gives you hands-on experience with [vLLM](https://github.com/vllm-project/vllm), a high-throughput LLM serving engine that uses PagedAttention (one of the required readings in this course). You will deploy a model, benchmark its performance, and observe how GPU parallelism affects serving throughput.

## Part 1: Setup and Single-GPU Serving

1. Install vLLM:
   ```bash
   pip install vllm
   ```

2. Start a vLLM server with a small model (e.g., `meta-llama/Llama-3.1-8B-Instruct`):
   ```bash
   vllm serve meta-llama/Llama-3.1-8B-Instruct --port 8000
   ```
   Note: You will need a [Hugging Face access token](https://huggingface.co/settings/tokens) with access to the Llama model. Set it via `export HF_TOKEN=your_token`.

3. In a separate terminal, send a test request:
   ```bash
   curl http://localhost:8000/v1/completions \
     -H "Content-Type: application/json" \
     -d '{"model": "meta-llama/Llama-3.1-8B-Instruct", "prompt": "Explain how PagedAttention works in 3 sentences.", "max_tokens": 128}'
   ```

## Part 2: Benchmarking

Keep the vLLM server from Part 1 running. In a separate terminal, use vLLM's built-in benchmarking tool to measure throughput and latency.

1. Run a benchmark against the serving endpoint:
   ```bash
   vllm bench serve \
     --model meta-llama/Llama-3.1-8B-Instruct \
     --dataset-name random \
     --request-rate 4 \
     --num-prompts 100
   ```

2. Vary the request rate (e.g., 1, 2, 4, 8, 16 requests/sec) and record:
   - Throughput (tokens/sec)
   - Mean and P99 time-to-first-token (TTFT)
   - Mean and P99 time-per-output-token (TPOT)

3. Plot throughput vs. latency as you increase the request rate. At what point does the system saturate?

## Part 3: Multi-GPU Tensor Parallelism

For this part, launch a multi-GPU instance (e.g., `g5.12xlarge` with 4x A10G).

1. Restart the server with tensor parallelism:
   ```bash
   vllm serve meta-llama/Llama-3.1-8B-Instruct --tensor-parallel-size 2 --port 8000
   ```

2. Re-run the same benchmarks from Part 2 and compare:
   - How does throughput change with 2 GPUs vs 1?
   - How does latency change?
   - Is the speedup linear? Why or why not?

## Questions to Think About

- What does the throughput-latency curve look like as you increase the request rate? Where does the system saturate and why?
- How does multi-GPU tensor parallelism affect throughput and latency compared to single-GPU? Is the speedup linear? Why or why not?
- What role does PagedAttention play in enabling high-throughput serving? What would happen without it?
- What are the communication overheads introduced by tensor parallelism, and how might they limit scaling?
