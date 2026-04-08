# Chain-of-Thought Reasoning – Simple Structured Example

## 1. Problem Statement

A person buys:
- 2 items costing ₹50 each  
- 1 item costing ₹30  

Find the total cost.

---

## 2. Without Chain-of-Thought (Direct Answer)

**Prompt:**
What is the total cost?

**Output:**
₹130  

---

## 3. With Chain-of-Thought (Step-by-Step Reasoning)

**Prompt:**
Solve the following problem step by step:

A person buys:
- 2 items costing ₹50 each  
- 1 item costing ₹30  

---

## 4. Reasoning Steps

Step 1: Calculate cost of 2 items  
→ 2 × 50 = 100  

Step 2: Cost of 1 item  
→ 30  

Step 3: Add total cost  
→ 100 + 30 = 130  

---

## 5. Final Answer

Total cost = ₹130  

---

## 6. Key Comparison

| Approach | Output Style | Clarity | Accuracy |
|----------|-------------|---------|----------|
| Without CoT | Direct answer | Low | Moderate |
| With CoT | Step-by-step reasoning | High | High |

---

## 7. Key Insight

- Chain-of-Thought breaks problems into smaller steps  
- Improves understanding and reduces errors  
- Especially useful for multi-step problems  

---

## 8. Teaching Tip

Chain-of-Thought =  
"First think → Then solve → Then answer"

```python
# Chain-of-Thought Prompt – Gemini (Simple Example)

## Python Example (Gemini API)

```python
import google.generativeai as genai

# Configure API Key
genai.configure(api_key="YOUR_API_KEY")

# Load Gemini model
model = genai.GenerativeModel("gemini-1.5-flash")

# Chain-of-Thought Prompt
prompt = """
Solve the following problem step by step:

A person buys:
- 2 items costing ₹50 each
- 1 item costing ₹30

First calculate each step, then give the final answer.
"""

# Generate response
response = model.generate_content(prompt)

# Print output
print(response.text)

```
