# langchain-gemini-starter

LangChain + Gemini: From Simple Chains to Conversational Memory

This project documents my step-by-step journey learning how to build AI applications using LangChain and Google Gemini.

Instead of jumping directly into complex agents, I started from the basics and gradually built up toward conversational memory systems.

The goal of this repository is to clearly demonstrate how chatbots evolve — from simple prompt execution to memory-aware conversations.

# Learning Progression

This repository follows a structured path:

Applying a Simple Chain with Gemini

Designing Prompt Templates and Constructing SequentialChains in LangChain

Implementing a Basic Chatbot Without Memory in LangChain

Integrating ConversationBufferMemory to Enhance Chatbots

Differentiating Context with ConversationBufferWindowMemory

Each step builds directly on the previous one.

# Applying a Simple Chain with Gemini

I started with the fundamentals:

Connecting to the Gemini model (gemini-2.0-flash)

Sending a simple prompt

Receiving a response

Understanding how llm.invoke() works

This step focused purely on:

Model initialization

Basic text generation

Understanding response objects

At this stage, there is no memory, no chaining logic — just a direct prompt-response interaction.

# Designing Prompt Templates and Constructing Sequential Chains

Next, I moved from single prompts to structured workflows.

Here I learned how to:

Create PromptTemplate

Pass dynamic variables (e.g., {topic})

Chain components together using:

Prompt → LLM → Output Parser

Then I built a sequential chain where:

The model generates creative ideas

The output is passed into a second prompt

The model summarizes those ideas

This demonstrated how LangChain allows outputs from one step to feed into another — forming reusable pipelines.

At this stage, I understood:

How data flows between components

How to compose chains

How to structure multi-step reasoning

Still — no memory yet.

# Implementing a Basic Chatbot Without Memory

Now I transitioned into chatbot behavior.

I created:

A prompt that accepts a name

A follow-up prompt asking if the model remembers the name

Two separate chains

Important realization:

The chatbot does not remember anything.

When I entered my name and then asked:

“Do you remember my name?”

The model had no context — because each call was independent.

This helped me understand a key principle:

By default, LLMs are stateless.

Each request is isolated unless we explicitly manage memory.

# Integrating ConversationBufferMemory to Enhance Chatbots

Next, I introduced memory using ConversationBufferMemory.

Here’s what changed:

A single conversational chain was created

Chat history was stored

The model now had access to previous messages

Now when I:

Introduced my name

Asked later if it remembered

The model could correctly recall it.

This demonstrated:

How chat history is stored

How memory is injected into prompts

How context affects model behavior

This is the first time the chatbot behaved like a real conversation.

# Differentiating Context with ConversationBufferWindowMemory

Finally, I explored memory limits using ConversationBufferWindowMemory.

Instead of remembering everything, I configured it to:

Keep only the last k interactions

This allowed me to demonstrate:

Context trimming

Memory window behavior

How older information is forgotten

After multiple topic changes, when I asked:

“Do you remember my name?”

The chatbot could no longer recall it — because the memory window had moved past that interaction.

This step highlights a very important concept in production systems:

Memory is not infinite. Context management matters.

# Key Concepts Learned

Through this progression, I understood:

How LLM calls work

How prompt templates structure inputs

How to build sequential chains

Why chatbots are stateless by default

How conversation memory is implemented

How windowed memory affects context retention

# Requirements

Python 3.10+

Google Cloud project

Gemini API enabled

Billing enabled (required for API access)

# Purpose of This Project

This repository serves as:

A beginner-friendly learning log

A structured introduction to LangChain

A practical exploration of conversational memory

A foundation for building more advanced agentic AI systems

It is intentionally beginner-level and focused on understanding core building blocks before moving into advanced architectures.

# Next Steps

Possible future improvements:

Migrating fully to RunnableSequences (since LLMChain is deprecated)

Adding tool usage

Implementing agents

Connecting to a simple frontend

Exploring vector memory and retrieval

This project represents my practical journey from:

Simple prompt execution
→ Structured chaining
→ Stateless chatbot
→ Memory-enhanced chatbot
→ Windowed conversational memory
