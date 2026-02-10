# Latest Updates

## v1.2.0 — February 2026

Big release! We've been busy hardening the network, squashing sybils, and making everything faster. Here's what's new.

### Stronger Network Integrity

We've significantly strengthened the network's ability to detect and limit bad actors. Honest miners benefit from fairer consensus scoring, and the system is now much harder to game. We'll leave it at that. 😉

### Automatic Validator Discovery

No more manual onboarding! Once a validator registers on the subnet and posts its IP to the chain, the Challenge API picks it up automatically. It also now verifies that discovered validators are actually running Loosh software at the required version — nodes that aren't get quietly sidelined until they upgrade, while up-to-date validators get challenges right away.

### Challenge Delivery — Way More Reliable

Restarts used to flood validators with a backlog of stale challenges. Not anymore. The pusher now drops anything too old, rate-limits catch-up traffic, and uses exponential backoff when validators are at capacity. Challenges that already exist on the validator are treated as delivered instead of retried endlessly.

### Health Checks — Fast & Concurrent

Health checks used to run one-by-one — painful when there are hundreds of validators on the chain. Now they run up to 20 in parallel, bail immediately on unreachable hosts, and use exponential backoff on validators that aren't responding. A full check cycle that used to take minutes now finishes in seconds.

### Better Evaluation Quality

The validator's evaluation engine got a major upgrade — a new multi-granularity quality scorer assesses relevance, coherence, prompt coverage, and reasoning depth using sentence embeddings. Garbage consensus prevention filters out coordinated low-quality responses *before* clustering, and high-quality unique answers earn a diversity bonus. The embedding model was also upgraded to `all-mpnet-base-v2` for richer semantic representations.

### Under the Hood

- Structured logging (`structlog`) across every module for cleaner, machine-readable logs
- Race conditions fixed in Fiber key caching and validator routing counters
- Proper cryptographic signing with Bittensor wallet keys
- Tiered weight-setting fallback so validators never get deregistered due to transient API failures
- Atomic database writes and deterministic query ordering

---

## Previous Updates

### Portal Enhancements
- New Resources page with dedicated sections for miners and validators
- Improved navigation with Resources link
- Enhanced markdown content support

### Leaderboard Features
- See top performers ranked by score, stake, or availability
- Real-time updates with configurable refresh intervals
- Quick access to full miner details

### Accessibility Improvements
- Full keyboard navigation support
- Screen reader optimizations
- Focus indicators in both light and dark modes

Check back regularly for the latest updates and announcements!
