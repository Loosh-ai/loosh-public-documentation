# Mining on Loosh — Subnet 78

Miners are the inference backbone of the Loosh network. You run an LLM, receive challenges from validators, and compete on the quality and speed of your responses. The best miners earn the most emissions — and the network uses your work to power real AI applications at [app.loosh.ai](https://app.loosh.ai).

## What Makes Loosh Mining Different

- **Model Agnostic** — Run whatever model fits your hardware. Loosh doesn't prescribe a specific model — it evaluates the quality of your output, not what produced it. vLLM, Ollama, llama.cpp, or any OpenAI-compatible server all work.
- **Consensus Scoring** — Your response isn't just compared against a reference answer. It's evaluated against the entire set of miner responses using semantic similarity, clustering, and outlier detection. Agreeing with the consensus earns rewards; outliers get filtered.
- **EMA-Based Rewards** — Your TAO emissions are based on an Exponential Moving Average of your scores over 24 hours. One great response won't spike your rewards, and one bad one won't tank them. **Consistency is king.**
- **Encrypted Communication** — All challenge/response traffic uses Fiber MLTS (RSA key exchange + Fernet encryption). Your responses are never sent in the clear.

## Hardware at a Glance

Your hardware determines which models you can run, which directly impacts response quality.

| Tier | GPU | Model Example | Backend |
|------|-----|---------------|---------|
| **Entry** | A10 24GB | Qwen2.5-7B-Instruct | vLLM |
| **Mid-Range** | A100 80GB | Qwen2.5-14B-Instruct | vLLM |
| **High-End** | 2× A100 80GB | Qwen2.5-72B-Instruct-AWQ | vLLM |
| **CPU Only** | None | Qwen2.5-7B-Instruct-GGUF | llama.cpp |

See [min_compute.yml](https://github.com/Loosh-ai/loosh-inference-miner/blob/main/min_compute.yml) for the full model allowlist with quantization options and detailed specs.

## How Your Rewards Are Calculated

Understanding the scoring system is essential for maximizing emissions:

1. **Validators embed your response** using sentence transformers and compare it against all other miner responses
2. **Outliers are filtered** — if your answer is off-topic or drastically different, it gets excluded before scoring
3. **Consensus alignment is measured** — how closely your response matches the cluster that most miners agree on
4. **Speed matters** — faster responses earn a bonus, but quality always comes first
5. **EMA smoothing** — your per-challenge scores are averaged over 24 hours (α=0.3), so your reward trajectory is gradual and stable

**What this means in practice:**

| Behavior | Impact |
|----------|--------|
| Consistent, quality responses | Builds a strong EMA → higher rewards |
| One great response | Only ~30% impact on your EMA |
| One bad response | Only ~30% penalty → gradual recovery |
| Frequent downtime | Missed challenges = missed EMA contributions |

**Bottom line:** Stay online, run a good model, and be consistent. That's the winning formula.

## LLM Backend Options

| Backend | GPU Required? | Auto-Started? | Best For |
|---------|---------------|---------------|----------|
| **vLLM** | Yes | ✅ by `run-miner.sh` | Production (fastest) |
| **Ollama** | Optional | ❌ start separately | Easy setup, quick testing |
| **llama.cpp** | No | ❌ runs in-process | CPU-only or low-resource |
| **Custom** | Varies | ❌ start separately | Any OpenAI-compatible server |

The repo is optimized for vLLM by default. If you use a different backend, you're responsible for starting and managing that server. The [Miner Quickstart](https://github.com/Loosh-ai/loosh-inference-miner/blob/main/docs/MINER_QUICKSTART.md) walks through every option.

## Getting Started

The quickest path from zero to mining:

1. **Create a wallet** and fund it with TAO (or test TAO from the [faucet](https://app.minersunion.ai/testnet-faucet))
2. **Register** on subnet 78 with `btcli subnet register`
3. **Post your IP** with `fiber-post-ip --netuid 78`
4. **Clone, install, configure** — `git clone`, `uv sync --extra vllm`, copy `env.example` to `.env`
5. **Start mining** — `./run-miner.sh` handles vLLM and the miner together

You should receive your first challenge within minutes. We strongly recommend starting on **testnet** first — it's free and the full evaluation pipeline is running there.

## Tips for Maximizing Emissions

- **Stay online 24/7** — Every missed challenge is a missed EMA contribution
- **Use the biggest model your hardware can handle** — Quality is the primary scoring signal
- **Keep response times low** — Speed earns a bonus on top of quality
- **Enable auto-updates** — The miner repo ships with an auto-update script for PM2 deployments so you stay current
- **Monitor your rank** — Use this portal's leaderboard to track your position relative to other miners
- **Test on testnet first** — Verify your setup end-to-end before committing real TAO

## Key Resources

| Resource | Link |
|----------|------|
| Full README | [loosh-inference-miner](https://github.com/Loosh-ai/loosh-inference-miner/blob/main/README.md) |
| Quickstart Guide | [MINER_QUICKSTART.md](https://github.com/Loosh-ai/loosh-inference-miner/blob/main/docs/MINER_QUICKSTART.md) |
| RunPod Deployment | [RUNPOD_DEPLOYMENT.md](https://github.com/Loosh-ai/loosh-inference-miner/blob/main/docs/RUNPOD_DEPLOYMENT.md) |
| Backend Details | [LLM Backends](https://github.com/Loosh-ai/loosh-inference-miner/blob/main/miner/core/llms/README.md) |
| Hardware & Model Specs | [min_compute.yml](https://github.com/Loosh-ai/loosh-inference-miner/blob/main/min_compute.yml) |
| Evaluation Process | [EVALUATION_PROCESS.md](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/docs/EVALUATION_PROCESS.md) |

## Need Help?

- **Discord**: [Join the conversation](https://discordapp.com/channels/799672011265015819/1351180661918142474)
- **GitHub Issues**: [loosh-inference-miner/issues](https://github.com/Loosh-ai/loosh-inference-miner/issues)
- **Email**: hello@loosh.ai

