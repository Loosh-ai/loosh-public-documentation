# What's New

Stay up to date with the latest features, improvements, and fixes to the Loosh AI Assistant.

---

## December 2024 Release Notes

### Persistent Memory System

Loosh utilizes a two-tier memory architecture to maintain continuity across user sessions. This system enables the agent to accumulate context, recall prior decisions, and minimize redundancy.

* **Architecture** A high-speed working memory handles active session context, while long-term storage manages summarized narrative entries and factual data via semantic search.
* **Management** Users can interface with the memory layer using natural language commands to store, retrieve, query, or purge specific datasets.

### Integrated Ethical Reasoning

The platform has transitioned from basic content filtering to a proactive ethical evaluation pipeline. Before execution, the system analyzes instructions through three sequential lenses:

1. **Rights Evaluator** Checks for non-derogable and contextual rights violations.
2. **Deontic Evaluator** Validates actions against prohibitions, obligations, and permissions.
3. **Virtue Evaluator** Scores actions based on character-based frameworks such as honesty and justice.

### Prompt Analysis and Safety

Loosh executes real-time intent classification and risk scoring to mitigate hazards. The system identifies and blocks categories including explicit content, illegal activities, and fraudulent behavior while providing transparent feedback for filtered requests.

### Distributed Execution Architecture

The core is now powered by a distributed, event-based architecture for enhanced scalability and observability.

* **Event Pipeline** Requests transition from the Event Gateway to the Dispatcher, which orchestrates cognitive services (reasoning, memory, and ethics) before synthesizing a response.
* **Observability** Every stage emits discrete events such as `thinking`, `tool_call`, and `generation` to a message fabric, visible via the events sidebar for end to end request tracing.

### UI and Documentation Enhancements

* **Navigation** A centralized More Info menu provides rapid access to documentation, FAQs, and release logs.
* **Rendering** Markdown support now includes GitHub flavored syntax highlighting and responsive tables for technical documentation.

---

## Coming Soon

We're always working on improvements. See our [what's coming](https://app.loosh.ai/whats-coming) page to see what's on the horizon.

---

## Previous Updates

### November 2024

* **Event Sidebar** - View real-time processing pipeline
* **Connection Status** - Live indicator for event stream
* **Dark Mode** - System-preference based theming

### October 2024

* **Initial Release** - Loosh AI Assistant beta launch
* **User Authentication** - Secure login system
* **Real-time Chat** - Interactive AI conversations

---

## Feedback

Have suggestions for new features? We'd love to hear from you! Contact our team with your ideas and feedback.

---

*Check back regularly for updates!*
