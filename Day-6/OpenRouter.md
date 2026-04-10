# Multi-Provider Access (OpenRouter)

## Overview
Multi-provider access refers to the ability to use multiple large language models (LLMs) from different providers (such as Claude, GPT, and Gemini) through a single unified interface.

Platforms like OpenRouter make this possible by acting as an abstraction layer between applications and multiple LLM providers.

---

## Claude vs GPT vs Gemini (High-Level Differences)

### Claude (Anthropic)
Claude models are known for:
- Strong reasoning and structured thinking
- Better handling of long documents
- Safer and more cautious outputs
- Strong summarization and analysis capabilities

Use cases:
- Document analysis
- Research tasks
- Long-form reasoning

---

### GPT (OpenAI)
GPT models are known for:
- Balanced reasoning and creativity
- Strong coding capabilities
- High versatility across tasks
- Good ecosystem and tooling support

Use cases:
- Software development
- Chatbots and agents
- General-purpose AI applications

---

### Gemini (Google)
Gemini models are known for:
- Strong multimodal capabilities (text, image, etc.)
- Tight integration with Google ecosystem
- Good performance in reasoning and factual tasks
- Competitive cost-performance balance in some variants

Use cases:
- Multimodal applications
- Search and information-heavy tasks
- Scalable production systems

---

## Using OpenRouter

OpenRouter provides a unified API layer that allows switching between multiple models without changing application logic.

Key features:
- Single API for multiple providers
- Easy model switching
- Standardized request format
- Centralized billing and usage tracking

---

## Switching Models

With OpenRouter, switching models typically requires only changing the model name.

Example concept:
- From GPT → Claude → Gemini
- No major code changes required
- Only model identifier is updated

This enables rapid experimentation and optimization.

---

## Cost per Token

LLMs are billed based on token usage:
- Input tokens (prompt)
- Output tokens (response)

Each model has different pricing:
- Premium models → higher cost, better quality
- Lightweight models → lower cost, faster responses

---

## Cost vs Quality Decisions

Choosing a model involves balancing:

### High Quality Models
- Better reasoning
- More accurate outputs
- Higher cost

### Low Cost Models
- Faster responses
- Lower cost per request
- Slightly reduced accuracy or depth

Decision factors:
- Task complexity
- Budget constraints
- Required accuracy
- Latency requirements

---

## Caching and Budget Awareness

### Caching
Caching stores previous responses to avoid repeated API calls for the same input.

Benefits:
- Reduces cost
- Improves response speed
- Minimizes redundant computations

---

### Budget Awareness
Production systems must track usage to avoid unexpected costs.

Strategies:
- Set token limits per request
- Monitor daily/monthly spend
- Use cheaper models for simple tasks
- Route complex tasks to premium models only when needed

---

## Summary
Multi-provider access using OpenRouter enables flexible switching between models like Claude, GPT, and Gemini. This allows developers to optimize for cost, performance, and quality. Effective systems use model routing, caching, and budget controls to build scalable and cost-efficient AI applications.

## For Lab Follow Below instruction

```python

1.Go to Openrouter website create API_KEY
2.Under Openrouter API_KEY usage
3.COPY the API_KEY u only see once so.
4.then copy the code below mentioned and then run in ur own machine or vscode

```

```python
import requests
import json

API_KEY = "YOURS OPENROUTER API KEY"

url = "https://openrouter.ai/api/v1/chat/completions"

headers = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json"
}

print("🤖 Chat started (type 'exit' to quit)\n")

while True:
    user_input = input("You: ")

    if user_input.lower() in ["exit", "quit"]:
        print("👋 Chat ended")
        break

    response = requests.post(
        url,
        headers=headers,
        json={
            "model": "openrouter/free",
            "messages": [{"role": "user", "content": user_input}]
        }
    )

    result = response.json()

    if "choices" in result:
        print("\n🤖 Bot:", result["choices"][0]["message"]["content"], "\n")
    else:
        print("\n⚠️ API Error:\n", result, "\n")


```
