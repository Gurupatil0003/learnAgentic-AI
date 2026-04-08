## Prompt

# Examples-Based Prompting (Agentic AI Context)

## 1. Overview
Examples-based prompting (also called few-shot prompting) is a technique where **input-output examples are provided to guide model behavior**.

In Agentic AI systems, this is critical for:
- Controlling agent behavior
- Standardizing outputs
- Improving reliability in multi-step workflows

---

## 2. Zero-Shot vs Few-Shot Prompting

### Zero-Shot Prompting
- No examples provided
- Agent relies entirely on pre-trained knowledge

Use Cases:
- Simple queries
- General-purpose tasks

Limitations:
- Less control over output format
- Higher variability

---

### Few-Shot Prompting
- Includes examples demonstrating expected behavior

Use Cases in Agents:
- Tool usage patterns
- Structured outputs (JSON, SQL, API calls)
- Workflow standardization

Advantages:
- Better consistency
- Reduced ambiguity
- Improved accuracy for complex tasks

---

## 3. Selecting Good Examples

In Agentic AI, examples should be:

### Relevant
- Closely match the target task
- Reflect real-world use cases

### Diverse
- Cover different scenarios and edge cases

### Minimal
- Avoid unnecessary examples (token efficiency)

### Structured
- Clearly separate input, reasoning (if needed), and output

---

## 4. Negative Examples

Negative examples show **what should NOT be done**.

Purpose:
- Prevent incorrect behaviors
- Reduce hallucinations
- Improve constraint adherence

Example:
- Incorrect API usage
- Invalid output formats

In agents, negative examples help enforce:
- Tool constraints
- Output validation rules

---

## 5. Formatting Patterns

Consistent formatting is critical for agent reliability.

Common patterns:

### Input-Output Format
Task: <input>  
Output: <expected result>

---

### Structured Format (for Agents)
```json
{
  "action": "search",
  "input": "flights to Delhi"
}
```

## Types of prompting 

# Prompting Techniques – Theory (Agentic AI)

## 1. Zero-Shot Prompting

### Definition
Zero-shot prompting is a technique where the model is given a **direct instruction without any examples**.

### Key Idea
The model relies entirely on its **pre-trained knowledge** to generate a response.

### Characteristics
- No prior examples provided  
- Fast and lightweight  
- Less control over output  

### Use Cases
- Simple queries  
- General-purpose tasks  
- Quick responses  

### Limitation
- Output may be inconsistent or less accurate for complex tasks  

---

## 2. Instruction-Based Prompting

### Definition
Instruction-based prompting involves providing **clear and explicit instructions** about what the model should do.

### Key Idea
The model performs better when the task is **well-defined and structured**.

### Characteristics
- Clear task description  
- Improves response quality  
- Easy to implement  

### Use Cases
- Content generation  
- Data extraction  
- Task automation  

### Limitation
- May still lack strict control over output format  

---

## 3. Few-Shot (Examples-Based) Prompting

### Definition
Few-shot prompting includes **a small number of input-output examples** to guide the model.

### Key Idea
The model learns the **pattern from examples** and applies it to new inputs.

### Characteristics
- Improves consistency  
- Reduces ambiguity  
- Helps in pattern learning  

### Use Cases
- Structured outputs  
- Classification tasks  
- Tool usage patterns  

### Limitation
- Too many or poor-quality examples can confuse the model  

---

## 4. Chain-of-Thought Prompting

### Definition
Chain-of-Thought prompting encourages the model to **generate intermediate reasoning steps** before the final answer.

### Key Idea
Breaking problems into steps improves **logical accuracy and transparency**.

### Characteristics
- Step-by-step reasoning  
- Better performance on complex tasks  
- Increased token usage  

### Use Cases
- Mathematical problems  
- Logical reasoning  
- Planning tasks in agents  

### Limitation
- Slower responses  
- Not needed for simple tasks  

---

## 5. Role-Based Prompting

### Definition
Role-based prompting assigns a **specific role or persona** to the model.

### Key Idea
The model adapts its responses based on the **assigned expertise or behavior**.

### Characteristics
- Improves tone and domain knowledge  
- Produces specialized outputs  

### Use Cases
- Expert systems  
- Domain-specific tasks  
- Simulation scenarios  

### Limitation
- May produce overly confident or biased outputs  

---

## 6. Constraint-Based Prompting

### Definition
Constraint-based prompting involves adding **rules or limitations** to control the output.

### Key Idea
Constraining the model improves **precision and relevance**.

### Characteristics
- Strong control over output  
- Reduces unwanted responses  

### Use Cases
- Filtering systems  
- Recommendation engines  
- Code generation  

### Limitation
- Over-constraining may limit creativity  

---

## 7. Contextual Prompting

### Definition
Contextual prompting provides **background information or user-specific details** to guide the model.

### Key Idea
More context leads to **more relevant and personalized outputs**.

### Characteristics
- Improves alignment with user needs  
- Enhances relevance  

### Use Cases
- Personalized recommendations  
- Conversational agents  
- User-aware systems  

### Limitation
- Too much context can increase noise and token usage  

---

## 8. Negative Prompting

### Definition
Negative prompting specifies **what the model should avoid** in its response.

### Key Idea
Explicitly defining restrictions helps reduce **undesired outputs**.

### Characteristics
- Improves output quality  
- Reduces hallucinations  

### Use Cases
- Safe code generation  
- Content filtering  
- Quality control  

### Limitation
- May not always fully eliminate unwanted behavior  

---

## 9. Structured Prompting

### Definition
Structured prompting enforces a **fixed format** (e.g., JSON, tables) for outputs.

### Key Idea
Ensures outputs are **consistent, predictable, and machine-readable**.

### Characteristics
- High consistency  
- Easy integration with systems  
- Reduces parsing errors  

### Use Cases
- API integration  
- Automation workflows  
- Agent tool-calling  

### Limitation
- Requires strict formatting discipline  

---

## 10. Iterative Prompting

### Definition
Iterative prompting involves **refining prompts step-by-step** based on previous outputs.

### Key Idea
Improvement happens through **continuous feedback and adjustment**.

### Characteristics
- Progressive refinement  
- Human-in-the-loop approach  

### Use Cases
- Content editing  
- Design workflows  
- Real-world agent systems  

### Limitation
- Requires multiple interactions  
- Increased time and cost  

---

## Summary

Prompting techniques are essential for controlling and improving model behavior in Agentic AI systems.

Each technique serves a different purpose:

- Zero-shot → Quick tasks  
- Instruction → Clear execution  
- Few-shot → Pattern learning  
- Chain-of-Thought → Reasoning  
- Role-based → Expertise simulation  
- Constraint → Output control  
- Contextual → Personalization  
- Negative → Error reduction  
- Structured → System integration  
- Iterative → Continuous improvement  

Effective prompt design combines multiple techniques to achieve **accuracy, consistency, and reliability**.


## 6. When Examples Help

Examples improve performance when:

- Tasks are ambiguous or underspecified  
- Output format must be strict (e.g., JSON, code)  
- Agents interact with tools or external systems  
- Multi-step workflows are involved  

---

## 7. When Examples Confuse the Model

Examples can degrade performance when:

- Too many examples increase token noise  
- Examples are inconsistent in format or logic  
- Irrelevant examples are included  
- Conflicting patterns exist within examples  

### Consequences

- Incorrect generalization  
- Format inconsistencies  
- Increased hallucinations  

---

## 8. Best Practices for Agentic AI

- Use minimal but high-quality examples  
- Maintain strict and consistent formatting  
- Combine examples with clear instructions  
- Validate outputs when using structured formats  
- Continuously refine examples based on agent performance  

---

## 9. Summary

- Examples-based prompting is critical for controlling agent behavior  
- Few-shot prompting improves reliability and consistency  
- Proper example selection and formatting are essential  
- Poorly designed examples can negatively impact performance


## Code practice

| Platform | Link |
|----------|------|
| <img src="https://colab.research.google.com/img/colab_favicon_256px.png" width="20"/> Prompt Eng Examples | [Open Notebook](https://colab.research.google.com/drive/1h6SJCkUInsc9sTypQ24iDbCSr2ljyvZe?usp=sharing) |
| <img src="https://cdn-icons-png.flaticon.com/512/5968/5968906.png" width="20"/> Medium | [Read Article](YOUR_MEDIUM_LINK_HERE) |
```python
from transformers import AutoProcessor, MusicgenForConditionalGeneration
from IPython.display import Audio, display

# Load model
processor = AutoProcessor.from_pretrained("facebook/musicgen-small")
model = MusicgenForConditionalGeneration.from_pretrained("facebook/musicgen-small")


# Prompt Examples with Definitions

prompts = [

    # 1. Zero-Shot Prompting
    # Definition: Asking the model directly without giving any examples
    "Lo-fi chill beats with soft drums",

    # 2. Instruction-Based Prompting
    # Definition: Clearly telling the model what to generate
    "Generate a relaxing piano melody with slow tempo",

    # 3. Role-Based Prompting
    # Definition: Assigning a role to control style/output
    "Act as a professional music composer and create a cinematic background score",

    # 4. Constraint-Based Prompting
    # Definition: Adding rules or limits to the output
    "Generate a short music track using only piano, no drums",

    # 5. Contextual Prompting
    # Definition: Giving background/use-case for better results
    "I am making a travel vlog. Generate happy background music",

    # 6. Negative Prompting (Workaround)
    # Definition: Mentioning what to avoid in output
    "Upbeat pop music with synths, avoid noise and distortion",

    # 7. Structured Prompting
    # Definition: Using a fixed format for better control
    """Genre: Rock
    Mood: Energetic
    Instruments: Guitar, Drums""",

    # 8. Few-Shot Prompting
    # Definition: Giving examples to teach the model pattern
    """Example:
    Input: happy
    Output: upbeat music

    Example:
    Input: sad
    Output: slow melody

    Now:
    Input: energetic
    Output:""",

    # 9. Combined Prompting (Best Practice)
    # Definition: Mixing multiple techniques for best results
    """Act as a music producer.
    Genre: Cinematic
    Mood: Inspirational
    Avoid: noise"""
]


# Generate Music
inputs = processor(
    text=prompts,
    padding=True,
    return_tensors="pt",
)

audio_values = model.generate(
    **inputs,
    max_new_tokens=256,
    do_sample=True
)


# Play Output
sampling_rate = model.config.audio_encoder.sampling_rate

for i, audio in enumerate(audio_values):
    print(f"Output {i+1}")
    display(Audio(audio.numpy(), rate=sampling_rate))
```
