# Frequently Asked Questions

Welcome to the Loosh AI FAQ. Here you'll find answers to common questions about our platform and technology.

---

## About Loosh

### What is Loosh?

Loosh is a **testbed and demonstration environment** for our agentic technologies. We are building services designed to support **autonomous agents and robots** — intelligent systems that can reason, plan, and take action in the real world.

This chat interface is a simple, accessible way for people to interact with and explore our underlying technology. While chat is just one interface, the same infrastructure powers more advanced agentic and robotic applications.

### Who is this for?

This demo environment is designed for:

- **Developers** exploring agentic AI capabilities
- **Researchers** interested in autonomous systems
- **Partners** evaluating our technology for integration
- **Early adopters** who want to experience the future of AI

### Is this a production system?

This is a **testbed environment** for demonstration and experimentation. While we strive for reliability, features may change and the system is optimized for showcasing capabilities rather than production workloads.

---

## Mode Selector

### What is the mode selector?

The mode selector allows you to choose how the AI processes your request. Different modes are optimized for different types of tasks.

### What is Basic Inference mode?

**Basic Inference** is designed for simple, straightforward requests that can be answered directly:

- Quick questions and answers
- Simple text generation
- Basic information retrieval
- Conversational responses

This mode provides fast responses for tasks that don't require complex reasoning or external interactions.

### What is Reasoning mode?

**Reasoning** mode is designed for more complex requests that may require:

- Multi-step problem solving
- Interaction with external services and tools
- Data analysis and synthesis
- Planning and decision-making
- Tasks that benefit from "thinking through" the problem

Reasoning mode uses advanced techniques to break down complex problems, consider multiple approaches, and provide more thorough responses. It may take longer but produces higher quality results for challenging tasks.

### Which mode should I use?

| Task Type | Recommended Mode |
|-----------|------------------|
| Quick questions | Basic Inference |
| Simple chat | Basic Inference |
| Complex analysis | Reasoning |
| Multi-step problems | Reasoning |
| Tasks requiring tools | Reasoning |
| Research and synthesis | Reasoning |

### Will there be more modes?

Yes! We will be introducing **new modes aligned with robotic and agentic systems**. These upcoming modes will be designed for:

- **Robotic control and planning** — Modes optimized for physical world interaction
- **Autonomous agent workflows** — Modes for long-running, goal-directed tasks
- **Multi-agent coordination** — Modes for systems involving multiple AI agents
- **Specialized domain expertise** — Modes tuned for specific industries or use cases

Stay tuned to our [Coming Soon](/whats-coming) page for updates on new modes and capabilities.

---

## Getting Started

### How do I start a conversation with the AI?

Simply type your message in the input field at the bottom of the chat interface and press Enter or click the send button. The AI will process your request and respond in real-time.

### What types of questions can I ask?

The Loosh AI can help with a wide range of tasks including:

- **General questions** - Ask about any topic and get informative responses
- **Writing assistance** - Get help drafting emails, documents, or creative content
- **Code help** - Ask programming questions or get code explanations
- **Analysis** - Request analysis of data, text, or ideas
- **Problem-solving** - Work through complex problems step by step

### Is my conversation history saved?

Your conversations are stored during your active session. For privacy and security, conversation history is not persisted long-term unless explicitly saved.

---

## Account & Authentication

### How do I create an account?

Currently, Loosh is in a closed beta. If you have an invite, you can sign in using the login button in the top right corner. If you don't have access yet, you can request an invite from the login page.

### What authentication methods are supported?

We support secure authentication through multiple providers. Check the login page for currently available options.

### How do I log out?

Click on your profile picture or name in the top right corner of the interface, then select "Sign Out" from the dropdown menu.

---

## Features

### What do the event indicators mean?

When you send a message, you may notice event indicators in the header:

- **Events Connected** (green) - Real-time event stream is active
- **Connecting** (yellow) - Establishing connection to event stream
- **Events Error** (red) - There was an issue with the event stream

### Can I view the AI's processing steps?

Yes! Click "Show Events" in the header to open the events sidebar. This shows the real-time processing pipeline, including thinking steps and intermediate results. This transparency is especially useful when using Reasoning mode to see how the AI approaches complex problems.

### What is the correlation ID?

Each conversation message is assigned a unique correlation ID for tracking. This helps debug issues and trace the complete flow of your request through our systems — the same infrastructure that would power autonomous agents in production.

---

## Troubleshooting

### The AI isn't responding - what should I do?

Try these steps:

1. Check the connection status indicator in the header
2. Refresh the page
3. Check your internet connection
4. If the issue persists, try logging out and back in

### Why is the response slow?

Response times can vary based on:

- The **mode** you've selected (Reasoning takes longer than Basic Inference)
- The complexity of your request
- Current system load
- External service interactions (in Reasoning mode)

Complex requests requiring multi-step reasoning or external tool use may take longer to generate.

### How do I report a bug or issue?

Please contact our support team with:

- A description of the issue
- The mode you were using
- Steps to reproduce the problem
- Your correlation ID if available
- Screenshots if applicable

---

## Privacy & Security

### Is my data secure?

The short answer is, no, your data is not secure. While all communications are encrypted, and we follow industry best practices for data protection. The demo environment is running on permissionless compute. That means that third parties may be exposed to your prompts. This is by design, as this is not only a testbed for our technologies but also a testbed for running on the bittensor platform. Anyone can run a miner on the platform, and the v1 codebase for our subnet can not control what miners do with that data. We will be interodcing trusted compute environments in future iterations to address this. See our roadmap for more information.

Additionally, we will be reviewing any and all interactions with the system for quality assurance, testing and potentially for model trainig or fine tuning.

So, while we're not selling your data, nor are we exposing your data to other users, your data will pass through third parties. So, use the platform to your heart's content, but don't add any personal or personally identifiable information into the system. We have implemented basic PII and sensitive data filtering, but we offer no warranty or guarantee of any kind in this regard. See our terms of service for more detail.


### What data do you collect?

We collect only what's necessary to provide the service, including:

- Account information (email, name)
- Conversation content for session functionality
- Usage analytics to improve the service
- User specific memories are saved in the memory system

### Can I delete my data?

Yes, you can request deletion of your account and associated data by contacting our support team. But as noted above, it is possible that that data was collected by other parties and we have no control over this.

---

## More Questions?

If you didn't find what you're looking for, check out our [Documentation](/docs) or reach out to our support team.
