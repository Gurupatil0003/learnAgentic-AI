```python

import os
from getpass import getpass

from agno.agent import Agent
from agno.models.groq import Groq ##int

##tools -->agno
from agno.tools.websearch import WebSearchTools
from agno.tools.wikipedia import WikipediaTools
os.environ["GROQ_API_KEY"]=getpass("enter groq key")

## Agent --LLM--gpt and Agno
agent=Agent(
    name="First Agent",
    model=Groq(id="openai/gpt-oss-120b"),
    tools=[WebSearchTools(),
           WikipediaTools()],
    instructions=[
        "Search the internet for the user's quetions",
        "Summarize the information simply.",
        "include source links in your answer."
    ],
    add_history_to_context=True,
    num_history_runs=3,
    markdown=True
)

agent.print_response("find the latest reserch paper on AI",
                     stream=True)
agent.print_response("Explain AI using wikipedia",
                    stream=True)




```
