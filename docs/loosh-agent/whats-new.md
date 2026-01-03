# What's New

Stay up to date with the latest features, improvements, and fixes to the Loosh AI Assistant.

---

## December 2024

### Memory and Remembering

Loosh has a sophisticated memory system that lets the agent remember your conversations, learn from past interactions, and build context over time. Think of it like having a conversation with someone who actually remembers what you talked about last week.

#### Why Memory Matters

Most AI assistants treat each conversation like it's starting from scratch. Loosh is different—it can remember important details, recall past decisions, and build on previous conversations. This means you don't have to repeat yourself, and the agent gets better at helping you over time. Whether you're working on a long-term project, building a relationship with the agent, or just want continuity in your conversations, memory makes everything feel more natural and useful.

#### How Memory Works

Loosh uses a two-tier memory system:

**Working Memory** is like the agent's short-term memory—it holds what the agent is actively thinking about right now. When you retrieve information, it automatically gets loaded into working memory so the agent can reference it quickly throughout your conversation.

**Long-term Memory** is where important conversations, facts, and experiences get stored permanently. The system automatically creates narrative summaries of your conversations, making them easy to search and recall later. It uses semantic search, so you can find memories even if you don't remember the exact words you used.

#### How to Prompt for Memory

The best part? You can talk to Loosh about memory just like you'd talk to a person. Here are some natural ways to use memory:

**To save something important:**

- "Remember that I prefer dark mode interfaces"
- "Save this conversation about our project planning"
- "I want you to remember that I'm allergic to peanuts"
- "Keep track of this decision: we're going with option A"

**To recall past conversations:**

- "What did we talk about last time?"
- "Do you remember when we discussed the budget?"
- "What was that idea I had about the website redesign?"
- "Remind me what we decided about the meeting schedule"
- "What have we covered so far in this project?"

**To search for specific information:**

- "Find everything we've discussed about [topic]"
- "What do you know about [subject]?"
- "Search for conversations where we talked about [keyword]"
- "What memories do you have related to [concept]?"

**To forget something:**

- "Forget our conversation about [topic]"
- "Delete everything related to [subject]"
- "I want to remove the memory about [thing]"
- "Clear out old conversations about [topic]"

**Pro tips:**

- Be specific when saving: "Remember that I prefer Python over JavaScript for backend work" is better than just "Remember my preferences"
- Use natural language—you don't need special commands or syntax
- The agent will automatically remember important parts of conversations, but you can explicitly ask it to remember something if it's particularly important
- When searching, try different phrasings—the semantic search will find related content even if the words don't match exactly

### Ethical Reasoning

Loosh agents have built-in ethical reasoning capabilities. They don't just follow instructions blindly—they think about whether something is appropriate, safe, and aligned with good judgment before acting.

#### Why Ethical Reasoning Matters

This isn't just about avoiding harmful content (though that's important too). Ethical reasoning means the agent can help you think through the implications of decisions, recognize when something might be problematic, and suggest better alternatives. It's like having a thoughtful colleague who will push back when something doesn't feel right, rather than just executing whatever you ask for.

This is especially valuable when you're working on complex problems where the "right" answer isn't always obvious, or when you want a second opinion on whether an approach is appropriate. The agent can help you catch potential issues before they become problems.

#### How Ethical Reasoning Works

Ethical evaluation happens automatically as part of the agent's decision-making process. Loosh uses three specialized ethical evaluators that work together to provide comprehensive ethical assessment:

**1. Rights Evaluator (First Pass)**

The rights evaluator acts as a weighted first pass, checking if an action violates fundamental rights. It uses a three-tier hierarchy:

- **Non-derogable rights** - Absolute rights that can never be violated (like the right to life, freedom from torture, human dignity). Any violation here immediately fails the evaluation.
- **Qualified rights** - Rights that can be limited only under strict conditions (like privacy, freedom of expression). These require strong justification.
- **Contextual rights** - Domain-specific rights (like healthcare, education) that consider resource constraints and contextual factors.

If any rights are violated, the evaluation fails immediately—rights protection is non-negotiable.

**2. Deontic Evaluator (Duty-Based)**

The deontic evaluator checks actions against rules and duties using deontological logic. It evaluates three types of rules:

- **Prohibitions** - Things that must not be done (hard constraints and ethical boundaries)
- **Obligations** - Things that must be done (duties and requirements)
- **Permissions** - Things that may be done (conditional allowances)

This evaluator acts as a short-circuit—if a prohibition is violated or an obligation isn't fulfilled, the action fails. It's like checking if you're following the rules before considering anything else.

**3. Virtue Evaluator (Character-Based)**

The virtue evaluator assesses actions based on character and virtue expression. It considers:

- **Virtues** - Character traits like honesty, compassion, courage, justice, wisdom
- **Vices** - Negative traits like dishonesty, cruelty, cowardice, greed
- **Cultural context** - How virtues are interpreted across different cultural frameworks (Western, Eastern, Universal)

This evaluator scores how well an action expresses virtues or vices, helping ensure the agent acts in ways that reflect good character, not just following rules.

**How They Work Together**
The evaluators run in sequence: Rights first (any violation = immediate failure), then Deontic (rule violations = failure), then Virtue (character assessment). This layered approach ensures actions respect fundamental rights, follow ethical rules, and express good character.

When the agent is uncertain, it will ask for clarification or defer to your judgment rather than making assumptions. It can also refuse requests that seem inappropriate, explaining which evaluator flagged the concern and why.

#### How to Prompt for Ethical Reasoning

You can engage with ethical reasoning in several ways:

**To get ethical feedback:**

- "Is it ethical to [do something]?"
- "What are the ethical considerations here?"
- "Should I be concerned about [potential issue]?"
- "Is this approach appropriate for [context]?"
- "What could go wrong ethically with this plan?"

**To explore implications:**

- "What are the potential ethical problems with this?"
- "Help me think through the ethics of [situation]"
- "Are there any red flags I should be aware of?"
- "What would be a more ethical way to approach this?"

**When the agent pushes back:**

- If the agent refuses a request, it will explain why—listen to its reasoning
- You can ask for alternatives: "What would be a better way to accomplish this?"
- You can provide more context: "Actually, here's why this is okay in my situation..."
- The agent respects your judgment but will flag concerns

**Pro tips:**

- The agent is designed to err on the side of caution—if it seems overly cautious, provide more context
- Ethical reasoning is contextual—what's appropriate in one situation might not be in another
- You can explicitly ask the agent to consider ethics even when it doesn't automatically do so
- The agent will help you think through trade-offs rather than just saying "no"

### Content Safety and Prompt Analysis

Loosh includes content safety filters and prompt analysis to help keep conversations appropriate and safe. The system analyzes your prompts before processing them and filters out potentially harmful content.

#### Why Content Safety Matters

Content safety protects everyone—you, other users, and the system itself. It helps prevent the generation of harmful, illegal, or inappropriate content. But it's not just about blocking bad things; the prompt analyzer also helps the system understand your intent better, which leads to more accurate and helpful responses.

The safety system is designed to be transparent—when something gets filtered, you'll understand why. This helps you adjust your requests and get better results.

#### How Content Safety Works

Before your prompt reaches the cognitive systems, it goes through analysis that:

- Classifies your intent
- Assesses potential risks
- Understands the context
- Scores the safety level

The system then routes your request through appropriate safety checks. Most prompts flow through normally, but potentially problematic ones may trigger warnings or be blocked with explanations.

**What gets filtered:**

- Adult or explicit sexual content
- Illegal activities or content
- Content intended to harm minors
- Fraud, scams, or identity theft attempts
- Content that incites violence

**Important to know:**

- No safety system is perfect—some inappropriate content might slip through
- The system may occasionally block legitimate content (false positives)
- Safety filters reduce risk but don't eliminate it
- For sensitive use cases, don't rely solely on automated safety

#### Understanding Content Safety

The content safety system is designed to protect everyone while still allowing legitimate use cases. Here's what to know:

**How the system works:**

The system analyzes your prompts to understand intent and context. Most legitimate requests flow through normally. The safety filters are most likely to trigger when:

- The intent is unclear or ambiguous
- The request could be interpreted multiple ways
- The context suggests potentially harmful use

**Transparency and limitations:**

When content is filtered, the system will explain why. This transparency helps you understand what happened and adjust your approach if needed. Keep in mind:

- The system prioritizes safety and may be cautious
- False positives can occur—legitimate content might occasionally be flagged
- The system is designed to err on the side of caution to protect users
- No automated safety system is perfect, so use your judgment for sensitive applications

**What this means for you:**

The safety system is there to help, not to block legitimate use. If you're using Loosh for research, education, creative work, or professional purposes, you should be able to do so naturally. The filters are most effective when they can understand your intent and context, which happens automatically when you're clear about what you're trying to accomplish.

### How Everything Works Together

Loosh uses a distributed, event-driven architecture that makes everything fast, transparent, and scalable. When you send a message, it flows through several components that work together seamlessly.

#### Why the Architecture Matters

This architecture means you get real-time visibility into what the agent is doing, fast responses, and a system that can scale to handle complex tasks. You can watch the agent think through problems, see which tools it's using, and understand how it arrives at answers. This transparency builds trust and helps you get better results.

The event-driven design also means the system can handle multiple users, complex workflows, and high loads without breaking a sweat. Everything is designed to be observable, so when something goes wrong (or right!), you can see exactly what happened.

#### How the System Works

Here's the journey your request takes:

1. **You send a message** → The Event Gateway receives it and checks authentication
2. **Gateway checks it** → Your request is safety checked and analyzed for intent and priority
2. **Gateway routes it** → Your request goes to the Dispatcher
3. **Dispatcher analyzes** → It figures out what you need chooses the best execution strategy, and prioritizes the request
4. **Cognitive Services process** → Specialized systems handle reasoning, memory, ethics, and more
5. **Results come back** → The Dispatcher synthesizes everything into a response
6. **You see it in real-time** → Events stream back through the message fabric and are consumed by interested systems

Throughout this process, every component logs events to the message fabric (our event streaming system), which means you can see the full execution pipeline in real-time through the events sidebar.

**The key components:**

- **Event Gateway** - Your entry point; handles authentication and streams events back to you
- **Dispatcher** - The orchestrator; figures out what needs to happen and coordinates everything
- **Cognitive Services** - The brain; handles reasoning, memory, ethics, and all the AI magic
- **Message Fabric** - The observability and event messaging layer; streams events so interested systems can act, react or observe. Surfaces events to user interfaces so you can see what's happening

#### How to Use This Transparency

**Watch the events sidebar:**

- Click "Show Events" to see what's happening in real-time
- Each event shows a step in the processing pipeline
- You can click events to see full details
- The correlation ID lets you trace a request end-to-end

**Understand what you're seeing:**

- `thinking` - The agent is analyzing your request
- `tool_call` - The agent is using a tool or service
- `tool_result` - A tool returned results
- `generation` - The agent is generating its response
- `complete` - Everything finished successfully

**Use it to debug:**

- If something goes wrong, check the events to see where it failed
- The correlation ID is your friend—include it when reporting issues
- You can see which tools the agent used and what they returned
- This helps you understand why the agent made certain decisions

**Pro tips:**

- The events sidebar is especially useful for complex requests
- You can see when the agent is using memory, calling external services, or doing multi-step reasoning
- If a response seems off, the events will show you what the agent was thinking
- This transparency helps you learn how to prompt more effectively

---

## New Information Pages

We've added new pages to help you get the most out of Loosh:

- **FAQs** - Answers to frequently asked questions
- **Documentation** - Comprehensive user guides
- **What's New** - You're looking at it!

Access these pages anytime from the "More Info" dropdown in the header.

### Improved Navigation

The header now includes a convenient "More Info" dropdown menu for quick access to help resources and documentation.

### Enhanced Markdown Rendering

Content pages now feature:

- Syntax highlighting for code blocks
- GitHub-flavored markdown support
- Responsive tables
- Beautiful typography

---

## Coming Soon

We're always working on improvements. see our <a href="https://app.loosh.ai/whats-coming" target="_blank">what's coming</a> page to see what's on the horizon:

---

## Previous Updates

### November 2024

- **Event Sidebar** - View real-time processing pipeline
- **Connection Status** - Live indicator for event stream
- **Dark Mode** - System-preference based theming

### October 2024

- **Initial Release** - Loosh AI Assistant beta launch
- **User Authentication** - Secure login system
- **Real-time Chat** - Interactive AI conversations

---

## Feedback

Have suggestions for new features? We'd love to hear from you! Contact our team with your ideas and feedback.

---

*Check back regularly for updates!*
