# Using LLM APIs (Theory)

## Overview
LLM APIs allow developers to interact with large language models programmatically. Instead of manually prompting a chat interface, APIs enable applications to send requests and receive structured responses that can be integrated into software systems.

Modern LLM APIs (including OpenAI-style and Gemini-based APIs) follow a standardized request-response pattern, making it easier to switch between models and providers.

---

## OpenAI-Compatible API Concept
Many LLM providers adopt an OpenAI-like interface to maintain consistency across platforms.

This means the API typically follows a common structure:
- A model is selected (e.g., GPT, Gemini variants)
- A list of messages is sent as input
- Generation parameters are configured (e.g., temperature)
- A structured response is returned

Even when using models like Gemini, frameworks such as LangChain abstract differences and provide a unified interface for developers.

---

## Request Structure (Conceptual)
An LLM API request generally contains the following components:

- **Model**: Specifies which AI model will process the request  
- **Messages**: A structured conversation history including roles such as system, user, and assistant  
- **Parameters**: Controls behavior of the model (creativity, randomness, output length, etc.)

This structure ensures that the model understands both context and instruction clearly.

---

## Key Parameters

### Model
Defines which language model will be used for inference. Different models may vary in:
- Speed
- Cost
- Reasoning ability
- Context length

---

### Messages
Messages represent the conversation flow. Each message typically includes:
- Role (system, user, assistant)
- Content (actual text input or output)

This allows the model to maintain context across interactions.

---

### Temperature
Temperature controls randomness in model outputs:
- Low temperature → more deterministic and consistent responses
- High temperature → more creative and diverse responses

It is commonly used to balance accuracy vs creativity depending on the use case.

---

## Response Structure
The response from an LLM API is typically structured, containing:
- Generated text output
- Metadata (tokens used, model info, etc.)
- Sometimes safety or usage information

This structured response allows easy integration into applications.

---

## Role of Frameworks (e.g., LangChain)
Frameworks like LangChain simplify working with LLM APIs by:
- Abstracting API differences between providers
- Managing prompts and memory
- Handling message formatting automatically
- Providing tools for chaining multiple LLM calls

This reduces complexity and speeds up development.

---

## Error Handling Concept
Since LLM APIs depend on network calls and external services, failures can occur due to:
- Network issues
- Invalid API keys
- Rate limits
- Model unavailability

Therefore, applications must implement proper error handling to ensure reliability.

---

## Summary
LLM APIs provide a structured way to interact with language models programmatically. By using standardized components like model selection, message-based input, and controllable parameters, developers can build scalable AI applications. Frameworks like LangChain further simplify integration, especially when working with multiple providers such as Gemini and OpenAI-compatible systems.


## For Lab 
```python
1.Open VScode
2.Create Workspace
3.Understand API_KEY ,Langchain Frame work and Gemini AI GOOGLE STUDIO
4.then add the code below mentioned
```

```python

import getpass
import os
from langchain_google_genai import ChatGoogleGenerativeAI

# Set up API key
if not os.environ.get("GOOGLE_API_KEY"):
    os.environ["GOOGLE_API_KEY"] = getpass.getpass("Enter API key for Google Gemini: ")

# Initialize model
model = ChatGoogleGenerativeAI(model="gemini-2.5-flash")

print("Chat started. Type 'exit' to stop.\n")

while True:
    user_input = input("You: ")

    if user_input.lower() in ["exit", "quit"]:
        print("Goodbye!")
        break

    response = model.invoke(user_input)
    print("Model:", response.content + "\n")

```
