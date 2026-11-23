
```python

!pip install -q -U crewai rich

import os
from getpass import getpass
from crewai import Agent, Task, Crew, Process, LLM
from rich.console import Console
from rich.panel import Panel


console = Console()

# 1. Groq API Key
os.environ["GROQ_API_KEY"] = getpass("Enter Groq API Key: ")

# 2. Connect Groq LLM
llm = LLM(
    model="qwen/qwen3.8-27b",
    base_url="https://api.groq.com/openai/v1",
    api_key=os.environ["GROQ_API_KEY"],
    custom_openai=True,
    temperature=0.3,
    max_tokens=400
)

print("Groq connected successfully!")

# 3. Create Agents

market_analyst = Agent(
    role="Market Analyst",
    goal="Evaluate the market potential of a startup idea",
    backstory="You are an expert in market research.",
    llm=llm,
    verbose=True
)

competitor_analyst = Agent(
    role="Competitor Analyst",
    goal="Analyze possible competitors and alternatives",
    backstory="You are an expert in competitor analysis.",
    llm=llm,
    verbose=True
)

startup_advisor = Agent(
    role="Startup Advisor",
    goal="Give a final startup recommendation",
    backstory="You are an experienced startup mentor.",
    llm=llm,
    verbose=True
)

# 4. Create Tasks

market_task = Task(
    description="""
    Analyze this startup idea: {idea}

    Give:
    1. Target customers
    2. Market opportunity
    3. Three challenges

    Keep it short.
    """,
    expected_output="Short market analysis",
    agent=market_analyst
)

competitor_task = Task(
    description="""
    Analyze possible competitors for: {idea}

    Give:
    1. Three possible competitors or alternatives
    2. Their advantages
    3. How this startup can be different

    Keep it short.
    """,
    expected_output="Short competitor analysis",
    agent=competitor_analyst
)

advisor_task = Task(
    description="""
    Review the previous two analyses for: {idea}

    Give:
    1. Is this idea worth building?
    2. Three features for the first version
    3. What should the founder do first?
    4. Final verdict: GO, IMPROVE, or AVOID

    Keep it practical and short.
    """,
    expected_output="Final startup validation report",
    agent=startup_advisor,
    context=[market_task, competitor_task]
)

# 5. Create Crew

startup_crew = Crew(
    agents=[
        market_analyst,
        competitor_analyst,
        startup_advisor
    ],
    tasks=[
        market_task,
        competitor_task,
        advisor_task
    ],
    process=Process.sequential,
    verbose=True
)

# 6. Get User Input

idea = input("\nEnter your startup idea: ")

console.print(
    Panel(idea, title="AI STARTUP VALIDATOR")
)

# 7. Execute Agents

print("\nStarting AI agents...\n")
# 7. Execute Agents asynchronously

print("\nStarting AI agents...\n")

result = await startup_crew.kickoff_async(
    inputs={"idea": idea}
)

# 8. Display Final Result

console.print(
    Panel(
        str(result),
        title="FINAL STARTUP REPORT",
        border_style="green"
    )
)



```
