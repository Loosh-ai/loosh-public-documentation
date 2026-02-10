# Validating on Loosh — Subnet 78

Validators are the quality engine of the Loosh network. You receive inference challenges, distribute them to miners, evaluate the responses, and set on-chain weights that determine who earns emissions. If miners are the muscle, validators are the brain.

## What Makes Loosh Validators Different

- **Automatic Discovery** — Register on subnet 78, post your IP with `fiber-post-ip`, and the Challenge API finds you. No manual onboarding, no waiting for approval.
- **Push-Based Challenges** — Challenges are pushed to you over Fiber MLTS (encrypted end-to-end). You don't poll for work.
- **Consensus-Based Evaluation** — You don't just pick a "best" answer. You cluster responses, compute semantic similarity, filter outliers, and score miners against the consensus.
- **EMA Scoring** — Weights are set using Exponential Moving Averages over a 24-hour window, so the network rewards consistency, not lucky one-offs.

## Hardware at a Glance

Validators don't run LLM inference, but they do run sentence-transformer embeddings on GPU for fast evaluation.

| Tier | GPU | CPU | RAM | Storage |
|------|-----|-----|-----|---------|
| **Minimum** | 16GB VRAM (T4+) | 4+ cores | 16GB | 100GB SSD |
| **Recommended** | 24GB VRAM (A10, RTX 3090+) | 8+ cores | 32GB | 250GB NVMe |

GPU matters here — it's the difference between evaluating a challenge in milliseconds vs. seconds, and that adds up fast at high volume.

## The One Thing You Must Not Forget

**Open your firewall.** Your validator receives challenges via inbound HTTPS from the Challenge API. If the port you posted to the chain isn't reachable from `challenge.loosh.ai` (mainnet) or `challenge-test.loosh.ai` (testnet), you will never receive challenges and will not earn emissions. The [Validator README](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/README.md) has example `ufw` and `iptables` rules.

## How Rewards Work

1. You evaluate miner responses and compute per-miner emission scores locally
2. Scores are stored in your local database immediately — even if the Challenge API is temporarily down
3. Every ~72 minutes, your validator computes EMA scores over the last 24 hours and sets weights on-chain
4. A tiered fallback strategy (Normal → Degraded → Emergency) ensures you never miss a weight-setting window and risk deregistration

For the full breakdown, see [WEIGHT_SETTING_FALLBACK_STRATEGY.md](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/docs/WEIGHT_SETTING_FALLBACK_STRATEGY.md).

## Getting Started

The quickest path from zero to validating:

1. **Create a wallet** and fund it with TAO (or test TAO from the [faucet](https://app.minersunion.ai/testnet-faucet))
2. **Register** on subnet 78 with `btcli subnet register`
3. **Post your IP** with `fiber-post-ip --netuid 78`
4. **Clone, install, configure** — `git clone`, `uv sync`, copy `env.example` to `.env`
5. **Open your firewall** for the Challenge API domain
6. **Start the validator** — via PM2, Docker, or direct execution

You should see challenges arriving within a few minutes. We strongly recommend starting on **testnet** first.

## Deployment Options

| Method | Best For | Auto-Restart? |
|--------|----------|---------------|
| **PM2** | Production on bare metal | ✅ Yes |
| **Docker** | Containerized / Kubernetes | ✅ Yes |
| **RunPod** | GPU cloud, no hardware to manage | ✅ Yes |
| **Scripts / Direct** | Testing and development | ❌ No |

All options are covered in detail in the [Validator Quickstart Guide](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/docs/VALIDATOR_QUICKSTART.md).

## Key Resources

| Resource | Link |
|----------|------|
| Full README | [loosh-inference-validator](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/README.md) |
| Quickstart Guide | [VALIDATOR_QUICKSTART.md](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/docs/VALIDATOR_QUICKSTART.md) |
| RunPod Deployment | [RUNPOD_DEPLOYMENT.md](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/docs/RUNPOD_DEPLOYMENT.md) |
| Evaluation Process | [EVALUATION_PROCESS.md](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/docs/EVALUATION_PROCESS.md) |
| Weight Setting Strategy | [WEIGHT_SETTING_FALLBACK_STRATEGY.md](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/docs/WEIGHT_SETTING_FALLBACK_STRATEGY.md) |
| Hardware Specs | [min_compute.yml](https://github.com/Loosh-ai/loosh-inference-validator/blob/main/min_compute.yml) |

## Need Help?

- **Discord**: [Join the conversation](https://discordapp.com/channels/799672011265015819/1351180661918142474)
- **GitHub Issues**: [loosh-inference-validator/issues](https://github.com/Loosh-ai/loosh-inference-validator/issues)
- **Email**: hello@loosh.ai