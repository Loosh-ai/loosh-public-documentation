# Frequently Asked Questions

Welcome to the Loosh AI FAQ — the fastest way to understand what you’re looking at, what it’s *not*, and why it exists.

---

## About Loosh

### So… this isn’t a chatbot?

Right. **Loosh Agent UI *looks* like a chat app because chat is the simplest front-end for demonstrating agentic behavior.** But the thing we’re actually building is **agentic + cognitive services for autonomous robotics** — systems that can *reason, plan, coordinate tools, and take action* in real environments.

If you come here expecting “ChatGPT, but with a different logo,” you’ll probably be disappointed. That’s not the goal, and we’re not optimizing for that use case.

### Okay then — what *is* it?

**This UI is a testbed.** A sandbox for trying out Loosh’s agentic stack as we build toward:

* **Cognitive services** that orchestrate perception/reasoning/planning loops
* **Autonomous robotics** workflows (decision-making, control pipelines, tool use, telemetry)
* **Agent infrastructure** (tracking, evaluation, memory, execution, coordination)

Not everyone has a robot on their desk to deploy our SDK to. So we built this interface as a place to **experience the underlying system** as it evolves.

### Who is this for?

This environment is most useful for:

* **Developers** exploring agentic workflows and tool orchestration
* **Researchers** interested in autonomous systems and decision loops
* **Partners** evaluating Loosh for integration into real products
* **Early adopters** who want to poke at “what’s next” (and don’t mind sharp edges)

### Is this production?

No. **This is a beta/demo environment** — a moving target.

* Features may change quickly (or disappear)
* You may see experimental behaviors
* Reliability is “demo reliable,” not “SLA reliable”
* Sometimes the UI is basically a skeleton for shipping the next thing

You’re welcome to use it — just know what you’re signing up for.

---

## Mode Selector

### What is the mode selector?

Modes control **how the system executes your request**. Think of it less like “personality” and more like selecting an execution strategy.

### What is Basic Inference mode?

**Basic Inference** is for straightforward requests that don’t need deep planning or tool chains:

* Quick Q&A
* Simple text generation
* Lightweight retrieval
* Casual interaction

It’s optimized for speed and simplicity.

### What is Reasoning mode?

**Reasoning** is for requests that benefit from multi-step thinking and orchestration:

* Multi-step problem solving
* Tool / service interaction
* Synthesis across sources
* Planning and decision-making
* Tasks where intermediate steps matter

It may be slower — because it’s actually *doing more*.

### Which mode should I use?

| Task Type              | Recommended Mode |
| ---------------------- | ---------------- |
| Quick questions        | Basic Inference  |
| Simple chat            | Basic Inference  |
| Complex analysis       | Reasoning        |
| Multi-step problems    | Reasoning        |
| Tasks requiring tools  | Reasoning        |
| Research and synthesis | Reasoning        |

### Will there be more modes?

Yes — and they’ll look increasingly “robot-shaped.”

Upcoming directions include:

* **Robotic control + planning** (physical-world interaction loops)
* **Goal-directed autonomous workflows** (long-running execution, retries, state)
* **Multi-agent coordination** (specialists, delegators, supervisors)
* **Domain-tuned execution modes** (industry-specific cognition + tools)

---

## Getting Started

### How do I start?

Type into the message box and hit Enter. That’s it.

If you want a better feel for what Loosh is good at, try prompts like:

* “Plan a workflow to accomplish X using tools, then execute step 1.”
* “Show your reasoning and intermediate steps.”
* “Use the available services to validate this claim / transform this data.”

### What types of questions can I ask?

You *can* ask general questions, but the platform shines when you ask for things like:

* **Plans, workflows, and tool use**
* **Reasoned decision-making** (“compare options, justify, select”)
* **Structured outputs** (schemas, steps, runnable plans)
* **Transparent execution** (watching what happens under the hood)

### Is my conversation history saved?

Your conversations are stored during your active session. **We do not persist long-term history by default** unless you explicitly save it (or a feature you’re using clearly indicates persistence).

---

## Account & Authentication

### How do I create an account?

Loosh is currently in **closed beta**. If you have an invite, sign in via the login button. If not, request access from the login page.

### What authentication methods are supported?

We support secure authentication through multiple providers. The login page will show what’s currently enabled.

### How do I log out?

Click your profile in the top-right corner and select **Sign Out**.

---

## Features

### What do the event indicators mean?

When you send a message, you’ll see connection status indicators:

* **Events Connected (green)** — live event stream is active
* **Connecting (yellow)** — establishing connection
* **Events Error (red)** — event stream issue detected

### Can I view what the system is doing?

Yes — and that’s kind of the point.

Click **Show Events** to open the event sidebar. You’ll see the execution pipeline in real time: planning steps, tool calls, intermediate outputs, and system decisions.

### What is the correlation ID?

Each message gets a **correlation ID** so we can trace the full lifecycle of your request through our services — the same type of tracing you’d want in production autonomous systems.

If you report a bug, include the correlation ID. It saves a lot of time.

---

## Troubleshooting

### The AI isn’t responding — what should I do?

Try:

1. Check the header connection indicator
2. Refresh the page
3. Verify your network connection
4. Log out and back in

If it still fails, send us the correlation ID and a screenshot.

### Why is the response slow sometimes?

Common reasons:

* **Reasoning mode** does more work than Basic Inference
* Your request requires multi-step planning
* The system is under load
* External services/tools are involved

If you want speed, keep requests small and use Basic Inference.

### How do I report a bug?

Send:

* What happened (and what you expected)
* Mode used (Basic / Reasoning)
* Steps to reproduce
* **Correlation ID**
* Screenshots (if helpful)

---

## Privacy & Security

### Is my data secure?

The short answer: **no — not in the way you’d expect from a traditional SaaS product.**

We do encrypt traffic and follow industry best practices where we can. But this **demo environment runs on permissionless compute**, which means **third parties may process (and therefore be exposed to) your prompts**. That’s intentional: Loosh is not only a testbed for our agentic technologies, it’s also a testbed for operating on the **[Bittensor](https://bittensor.com/)** platform.

Because **anyone can run a miner**, and the current **v1 subnet codebase can’t control what miners do with data**, we can’t offer strong guarantees about confidentiality today. We plan to introduce **trusted compute environments** in future iterations to address this — see the roadmap for where that’s headed.

Also: we may review interactions for **quality assurance, testing, and potentially for model training or fine-tuning**.

So while we’re **not selling your data**, and we’re **not exposing your data to other Loosh users**, your data **may pass through third parties**.

**Use the platform freely — but don’t include personal, confidential, or personally identifiable information (PII).** We’ve implemented basic PII/sensitive-data filtering, but we provide **no warranty or guarantee** that it will catch everything. See our Terms of Service for details.


### What data do you collect?

We collect what we need to run and improve the system, such as:

* Account info (email, name)
* Conversation content for session functionality
* Usage analytics to improve the product

### Can I delete my data?

Yes — contact support to request deletion of your account and associated data.

---

## More questions?

If you didn’t find what you need, check our Documentation or reach out to support.
