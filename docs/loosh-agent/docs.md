# Documentation

Welcome to the Loosh AI Assistant documentation. This guide covers everything you need to know to get the most out of the platform.

---

## Overview

Loosh is an advanced AI assistant designed to help you with a variety of tasks. The platform combines powerful language models with a real-time event-driven architecture to provide responsive, transparent AI interactions.

### Key Features

- **Real-time Processing** - Watch the AI think through problems in real-time
- **Event Transparency** - Full visibility into the processing pipeline
- **Secure Authentication** - Enterprise-grade security for your conversations
- **Modern Interface** - Clean, responsive design that works on any device

---

## Quick Start

### 1. Sign In

Click the login button in the top right corner and authenticate with your credentials. If you don't have an account, you can request an invite.

### 2. Start a Conversation

Type your message in the input field at the bottom of the screen. Press Enter or click the send button to submit.

### 3. View the Response

The AI's response will appear in the chat area. You can continue the conversation by sending additional messages.

### 4. Monitor Events (Optional)

Click "Show Events" to see the real-time processing pipeline in the sidebar.

---

## User Interface

### Chat Area

The main chat area displays your conversation with the AI:

- **User messages** - Displayed on the right with your avatar
- **AI responses** - Displayed on the left with the Loosh icon
- **Thinking indicator** - Shows when the AI is processing

### Header

The header contains:

| Element | Description |
|---------|-------------|
| Logo | Click to return to the main chat |
| More Info | Dropdown with links to FAQs, Docs, and What's New |
| User Menu | Your profile and sign out option |
| Connection Status | Real-time connection indicator |
| Event Count | Number of events for current request |

### Events Sidebar

When enabled, the events sidebar shows:

- **Correlation ID** - Unique identifier for the request
- **Event Stream** - Real-time list of processing events
- **Event Details** - Click an event to see full details

---

## Chat Commands

While there are no special commands required, here are some tips for effective prompting:

### Be Specific

> **Good:** "Write a Python function that calculates the factorial of a number using recursion"
> 
> **Less effective:** "Write some code"

### Provide Context

> **Good:** "I'm building a React app and need help with state management. Currently using useState but considering Redux. What do you recommend?"
> 
> **Less effective:** "Redux vs useState?"

### Ask Follow-up Questions

The AI remembers your conversation context, so you can ask follow-up questions:

1. "Explain how async/await works in JavaScript"
2. "Can you show me an example with error handling?"
3. "How would this differ in TypeScript?"

---

## Event Types

The events sidebar displays various event types during processing:

### Execution Events

These events show the AI's processing steps:

- `thinking` - AI is analyzing the request
- `tool_call` - AI is invoking a tool or function
- `tool_result` - Result from a tool invocation
- `generation` - AI is generating the response

### Completion Events

These mark the end of processing:

- `complete` - Request processed successfully
- `error` - An error occurred during processing

---

## Configuration

### Environment Variables

For developers, the following environment variables are available:

```bash
# Event Gateway
NEXT_PUBLIC_EVENT_GATEWAY_URL=http://localhost:8000/events
NEXT_PUBLIC_EVENT_GATEWAY_API_KEY=your-api-key

# WebSocket Proxy
NEXT_PUBLIC_WS_PROXY_URL=ws://localhost:9005
NEXT_PUBLIC_EXECUTION_TOPIC=agent-execution-events
NEXT_PUBLIC_COMPLETION_TOPIC=agent-completed-events

# Markdown Cache Duration (default: 30 minutes)
NEXT_PUBLIC_MARKDOWN_CACHE_DURATION_MS=1800000
```

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Enter` | Send message |
| `Shift + Enter` | New line in message |

---

## API Integration

For developers looking to integrate with the Loosh platform, please contact our team for API documentation and access credentials.

---

## Best Practices

### For Better Results

1. **Start with clear goals** - Know what you want to accomplish
2. **Iterate** - Refine your prompts based on responses
3. **Use examples** - Show the AI what format you want
4. **Break down complex tasks** - Split large requests into steps

### For Secure Usage

1. **Don't share credentials** - Keep your login details private
2. **Review sensitive content** - Check AI outputs before sharing
3. **Log out on shared devices** - Protect your session

---

## Support

Need help? Here are your options:

- **FAQs** - Check our [Frequently Asked Questions](/faqs)
- **What's New** - See the [latest updates](/whats-new)
- **Contact** - Reach out to our support team

---

*Last updated: December 2024*

